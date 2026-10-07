# dataset-generator

## Dataset versions (releases)

Datasets are produced **only by releases**: pushing a `v*` tag (GitHub release) runs
`.github/workflows/publish-to-kaggle.yml`, which runs `main.py` and uploads a new version of the Kaggle dataset
[`skykuba/kegg-pathway-images`](https://www.kaggle.com/datasets/skykuba/kegg-pathway-images).

> [!IMPORTANT]
> The code on `main` may not reflect the **latest** release. To know how a given dataset was generated, look at the
> code **at its tag** (`git checkout <tag>`), not at `main`. Different releases may use different normalisations.

| Tag | Normalisation | Notes |
|---|---|---|
| `v1.1.0` | Custom: `log1p` + two-stage min–max (95th-percentile threshold) → integers 2…255, zero counts → 1 (`src/normalize_data.py`) | First release with labels mapped by sample `id` (PR #16) |
| `v1.1.1` | DESeq2 size factors + VST, fast mode (`fit_size_factors`, `vst(fit_type="mean")`) | PR #20 |
| `v1.1.2` | DESeq2 full workflow (`deseq2()`) + VST | PR #21 |

Releases before `v1.1.0` assign labels by position (36 mislabelled files) and should not be used.

## Code Quality & Formatting

This project uses **[Black](https://github.com/psf/black)** for code formatting and **[Pylint](https://pylint.pycqa.org/)** for static code analysis.

### Setup & Dependencies

Install all dependencies including development tools:

```bash
pip install -r requirements.txt
```

### Formatting Code

All Python code should be formatted using `black` before pushing changes:

```bash
black .
```

To check formatting without making changes:

```bash
black --check .
```

### Running Pylint

To analyze code quality locally with Pylint:

```bash
pylint $(git ls-files '*.py')
```