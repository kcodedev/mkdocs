# Typer: Modern Python CLI Library

## What is Typer?

Typer is a modern, fast, and intuitive library for building command-line interfaces (CLIs) in Python. It leverages Python's type hints to automatically generate CLI interfaces, making it easier to create robust command-line applications without boilerplate code. Typer is built on top of Click, a popular CLI library, but provides a more Pythonic and type-safe approach.

## Key Features

- **Type Hints Integration**: Uses Python's type hints to define command parameters automatically
- **Automatic Help Generation**: Generates help text and usage information from function signatures
- **Subcommands Support**: Easily create nested command structures
- **Shell Completion**: Supports auto-completion for bash, zsh, and fish
- **Modern Python**: Designed for Python 3.6+ with full type hint support
- **FastAPI-like Syntax**: Familiar syntax if you've used FastAPI

## Installation

Install Typer using pip:

```bash
pip install typer
```

For shell completion support:

```bash
pip install typer[all]
```

## Basic Usage

### Simple Command

Here's a basic example of a Typer application:

```python
import typer

def main(name: str):
    typer.echo(f"Hello {name}!")

if __name__ == "__main__":
    typer.run(main)
```

Run it:

```bash
python script.py "World"
# Output: Hello World!
```

### Using Typer App

For more complex applications, use the `Typer` class:

```python
import typer

app = typer.Typer()

@app.command()
def hello(name: str):
    typer.echo(f"Hello {name}!")

@app.command()
def goodbye(name: str, formal: bool = False):
    if formal:
        typer.echo(f"Goodbye, {name}. Have a good day.")
    else:
        typer.echo(f"See ya, {name}!")

if __name__ == "__main__":
    app()
```

This creates two commands:

```bash
python script.py hello "Alice"
# Output: Hello Alice!

python script.py goodbye "Bob" --formal
# Output: Goodbye, Bob. Have a good day.
```

## Advanced Features

### Options and Arguments

```python
import typer

app = typer.Typer()

@app.command()
def create_user(
    username: str = typer.Argument(..., help="The username for the new user"),
    email: str = typer.Option(None, help="Email address for the user"),
    age: int = typer.Option(18, help="Age of the user"),
    admin: bool = typer.Option(False, "--admin", help="Make user an admin")
):
    typer.echo(f"Creating user: {username}")
    if email:
        typer.echo(f"Email: {email}")
    typer.echo(f"Age: {age}")
    typer.echo(f"Admin: {admin}")

if __name__ == "__main__":
    app()
```

### Subcommands

```python
import typer

app = typer.Typer()
users_app = typer.Typer()
app.add_typer(users_app, name="users")

@users_app.command("create")
def create_user(username: str):
    typer.echo(f"Creating user: {username}")

@users_app.command("delete")
def delete_user(username: str):
    typer.echo(f"Deleting user: {username}")

@app.command()
def config(setting: str, value: str):
    typer.echo(f"Setting {setting} to {value}")

if __name__ == "__main__":
    app()
```

Usage:

```bash
python script.py users create "alice"
python script.py config database "sqlite://db.sqlite"
```

### Type Validation

Typer automatically validates types based on your type hints:

```python
import typer
from enum import Enum

class Color(str, Enum):
    RED = "red"
    GREEN = "green"
    BLUE = "blue"

app = typer.Typer()

@app.command()
def paint(color: Color):
    typer.echo(f"Painting with {color.value}")

if __name__ == "__main__":
    app()
```

## What is Typer Good For?

1. **Rapid CLI Development**: Quickly build command-line tools with minimal code
2. **Type Safety**: Leverage Python's type system for robust CLI interfaces
3. **Script Automation**: Create reusable scripts with proper argument handling
4. **DevOps Tools**: Build deployment, configuration, and management tools
5. **Data Processing Pipelines**: Create command-line interfaces for data workflows
6. **Educational Tools**: Build interactive learning applications
7. **API Clients**: Create CLI clients for REST APIs or other services

## Comparison with Other CLI Libraries

- **vs Click**: Typer is built on Click but adds type hints and modern Python features
- **vs argparse**: More powerful and feature-rich than standard library argparse
- **vs docopt**: Uses type hints instead of docstring parsing
- **vs Fire**: Similar goal but Typer provides more control and better help generation

## Best Practices

1. Use descriptive parameter names and help text
2. Leverage type hints for automatic validation
3. Use `typer.Option` for optional parameters and `typer.Argument` for required positional arguments
4. Group related commands using subcommands
5. Add shell completion for better user experience
6. Use `typer.echo()` instead of `print()` for consistent output

## Example: File Organizer CLI

```python
import typer
from pathlib import Path
import shutil

app = typer.Typer()

@app.command()
def organize(
    source: Path = typer.Argument(..., help="Source directory to organize"),
    dest: Path = typer.Option(None, help="Destination directory (defaults to source)"),
    extensions: list[str] = typer.Option([], "--ext", help="File extensions to organize")
):
    """Organize files in a directory by extension."""
    if dest is None:
        dest = source

    if not source.exists():
        typer.echo(f"Source directory {source} does not exist", err=True)
        raise typer.Exit(1)

    for file_path in source.iterdir():
        if file_path.is_file():
            if extensions and file_path.suffix not in extensions:
                continue

            ext_dir = dest / file_path.suffix[1:]  # Remove the dot
            ext_dir.mkdir(exist_ok=True)
            shutil.move(str(file_path), str(ext_dir / file_path.name))
            typer.echo(f"Moved {file_path.name} to {ext_dir}")

if __name__ == "__main__":
    app()
```

This example demonstrates a practical CLI tool for organizing files by extension, showcasing Typer's ability to handle file paths, options, and provide helpful error messages.