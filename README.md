# dataset-generator

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