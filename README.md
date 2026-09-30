# playwright-python-practice

Portfolio project for UI test automation with **Python 3.14+**, **pytest**, **pytest-playwright** (sync API), and the **Page Object Model**.

## Stack

- Python 3.14+
- [uv](https://docs.astral.sh/uv/) for Python, virtualenv, and dependency management
- pytest + pytest-playwright
- Playwright (Chromium)
- Page Object Model under `pages/`

## Setup

Install uv (see the [install guide](https://docs.astral.sh/uv/getting-started/installation/)), e.g. `brew install uv`. Then:

```bash
uv sync
uv run playwright install chromium
```

`uv sync` installs the Python version from `.python-version`, creates `.venv`, and installs the exact versions locked in `uv.lock`.

## Run tests

```bash
uv run pytest
```

Single file (stop on first failure):

```bash
uv run pytest tests/test_login.py -x
```

Headed, slowed down for debugging:

```bash
uv run pytest --headed --slowmo 500
```

Optional lint/format:

```bash
uvx ruff check --fix . && uvx ruff format .
```

## Managing dependencies

```bash
uv add <package>          # runtime/test dependency
uv add --dev <package>    # dev-only tool
uv lock --upgrade         # upgrade locked versions
```

Commit `pyproject.toml` and `uv.lock` together.

## Layout

```
pages/            # Page Objects (one class per page; components/ for shared UI)
tests/            # test_<feature>.py
conftest.py       # shared fixtures
pytest.ini        # pytest config, markers, base_url
pyproject.toml    # project metadata and dependencies
uv.lock           # locked dependency versions
.python-version   # Python version used by uv
```
