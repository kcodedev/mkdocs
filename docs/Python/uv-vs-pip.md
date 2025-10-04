# uv vs pip

uv is a modern Python package installer and resolver, written in Rust, designed as a drop-in replacement for pip.

## What is uv?

uv is developed by Astral (the creators of Ruff) to provide a faster and more reliable alternative to pip. It aims to solve common issues with pip, such as slow installations and dependency resolution problems.

## Key Features of uv

- **Performance**: Significantly faster than pip due to its Rust implementation.
- **Dependency Resolution**: Uses a more advanced resolver that handles complex dependency trees better.
- **Virtual Environments**: Built-in support for creating and managing virtual environments.
- **Lock Files**: Supports lock files for reproducible and deterministic installations.
- **Drop-in Replacement**: Can be used as a direct replacement for pip in most cases.

## Comparison with pip

| Feature | uv | pip |
|---------|----|-----|
| Language | Rust | Python |
| Speed | Very fast | Slower |
| Dependency Resolution | Advanced (resists backtracking) | Basic (can have resolution failures) |
| Virtual Environment Support | Built-in (`uv venv`) | External (`python -m venv`) |
| Lock Files | Yes (`uv.lock`) | No |
| Installation Command | `uv pip install` | `pip install` |
| Global Installation | `uv tool install` | `pip install --user` or system-wide |

## Installation

Install uv using the official installer:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Or using pip (ironically):

```bash
pip install uv
```

## Basic Usage

### Installing packages
```bash
# Instead of pip install requests
uv pip install requests
```

### Creating virtual environments
```bash
uv venv myenv
source myenv/bin/activate  # On Unix
# myenv\Scripts\activate    # On Windows
```

### Installing in a project
```bash
# Initialize a project with uv
uv init myproject
cd myproject
uv add requests
```

## uv Commands Explained

### uv pip install vs uv add

- **`uv pip install`**: Installs packages into the current Python environment, just like `pip install`. It's a drop-in replacement that uses uv's faster resolver and better dependency resolution. Use this when you want to install packages globally or in an existing venv.

- **`uv add`**: Adds dependencies to a uv-managed project. It updates `pyproject.toml` with the new dependency and creates/updates `uv.lock` for reproducible installs. This is for project-based package management, similar to `poetry add` or `npm install`. Use this in uv projects for better dependency management.

### Virtual Environment Auto-Creation

uv does **not** automatically create virtual environments. You must explicitly create them using `uv venv`. However:

- `uv init` creates a new project and automatically sets up a virtual environment in `.venv`.
- In existing projects with a `.venv` directory, uv commands will use that environment if activated.
- uv does not auto-create venvs for arbitrary commands; you need to run `uv venv` first or use `uv init` for new projects.

## Advantages of uv over pip

1. **Speed**: Installations are typically 10-100x faster.
2. **Reliability**: Better dependency resolution avoids "resolution impossible" errors.
3. **Reproducibility**: Lock files ensure consistent installations across environments.
4. **Integrated Workflow**: Combines package management with virtual environment management.

## When to use pip vs uv

- **Use uv** for new projects, performance-critical installations, or when you need reliable dependency resolution.
- **Use pip** if you're working in environments where uv isn't available or for legacy projects.

## Migration from pip to uv

uv can often be used as a drop-in replacement:

```bash
# Replace pip with uv pip
alias pip='uv pip'
```

However, for full uv features, consider migrating to `uv add` for new dependencies.