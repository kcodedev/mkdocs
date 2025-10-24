# MK Docs read me

## Installation

First, install `uv` if not already installed. You can install it via:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Or follow the official installation guide at https://docs.astral.sh/uv/getting-started/installation/.

## Setup

Run MkDocs using `uv`:

```bash
uv run mkdocs serve
uv run mkdocs serve -a 0.0.0.0:8001
```

`uv run` will automatically handle the virtual environment and dependencies.
