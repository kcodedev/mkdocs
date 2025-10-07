# Python Imports in Docker Containers

## Why Relative Imports Fail in Docker

Relative imports in Python can fail inside Docker containers due to differences in how the Python interpreter resolves module paths compared to running code locally. This commonly occurs because:

### 1. Working Directory Issues
When running Python code in a container, the working directory might not be what you expect. Docker containers often start with `/` as the working directory unless explicitly set with `WORKDIR`.

```python
# This works locally but fails in Docker
from .utils import helper_function  # ModuleNotFoundError in container
```

### 2. PYTHONPATH Configuration
Containers don't automatically inherit your local `PYTHONPATH`. The Python interpreter in the container only knows about the standard library and installed packages, not your project structure.

### 3. Module Resolution Context
Python's relative import resolution depends on the `__name__` attribute of the executing script. When you run `python app/main.py` in a container, `__name__` becomes `__main__` instead of `app.main`, breaking relative imports.

## Common Failure Scenarios

### Running Scripts Directly
```bash
# This often fails in containers
docker run myapp python app/main.py
```

The script runs as `__main__` rather than as part of a package, causing relative imports to fail.

### Entrypoint Without Proper Setup
```dockerfile
FROM python:3.9
COPY . /app
CMD ["python", "app/main.py"]  # Relative imports break here
```

### Multi-Stage Builds
In multi-stage builds, the final image might not preserve the correct directory structure or Python path configuration.

## Solutions

### 1. Set Proper Working Directory
Always use `WORKDIR` in your Dockerfile to establish a consistent working directory:

```dockerfile
FROM python:3.9
WORKDIR /app
COPY . /app
CMD ["python", "-m", "app.main"]
```

### 2. Use Module Execution
Instead of running scripts directly, execute them as modules:

```bash
# Instead of: python app/main.py
# Use: python -m app.main
docker run myapp python -m app.main
```

### 3. Configure PYTHONPATH
Add your project root to Python's module search path:

```dockerfile
FROM python:3.9
ENV PYTHONPATH=/app
WORKDIR /app
COPY . /app
CMD ["python", "-m", "app.main"]
```

### 4. Use Entrypoint Scripts
Create an entrypoint script that sets up the environment:

```bash
#!/bin/bash
cd /app
export PYTHONPATH=/app
exec python -m app.main
```

```dockerfile
FROM python:3.9
COPY . /app
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
```

### 5. Restructure to Absolute Imports
Convert relative imports to absolute imports where possible:

```python
# Instead of relative imports
from .utils import helper_function
from ..models import User

# Use absolute imports
from myapp.utils import helper_function
from myapp.models import User
```

## Complete Examples

### Basic Flask Application
```
myapp/
├── app/
│   ├── __init__.py
│   ├── main.py
│   └── utils.py
├── Dockerfile
└── requirements.txt
```

```dockerfile
# Dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
ENV PYTHONPATH=/app
EXPOSE 5000
CMD ["python", "-m", "app.main"]
```

```python
# app/main.py
from flask import Flask
from .utils import setup_app  # This works with PYTHONPATH set

app = Flask(__name__)
setup_app(app)

if __name__ == "__main__":
    app.run(host="0.0.0.0")
```

### FastAPI Application with Docker Compose
```yaml
# docker-compose.yml
version: '3.8'
services:
  api:
    build: .
    ports:
      - "8000:8000"
    environment:
      - PYTHONPATH=/app
    command: python -m app.main
```

```dockerfile
# Dockerfile
FROM python:3.9
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . /app
ENV PYTHONPATH=/app
```

### Multi-Service Application
For applications with multiple services, ensure each service has its own proper Python path:

```dockerfile
# api/Dockerfile
FROM python:3.9
WORKDIR /app
ENV PYTHONPATH=/app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . /app
CMD ["python", "-m", "api.main"]

# worker/Dockerfile
FROM python:3.9
WORKDIR /app
ENV PYTHONPATH=/app
COPY requirements-worker.txt .
RUN pip install -r requirements-worker.txt
COPY . /app
CMD ["python", "-m", "worker.tasks"]
```

## Best Practices

1. **Always set WORKDIR** in your Dockerfile to establish a consistent working directory
2. **Use `python -m`** instead of direct script execution for better module resolution
3. **Set PYTHONPATH** explicitly in your container environment
4. **Prefer absolute imports** over relative imports for better maintainability
5. **Test imports** during the build process to catch issues early
6. **Use entrypoint scripts** for complex setup requirements
7. **Document your package structure** clearly in README files

## Troubleshooting

### Check Current Working Directory
```bash
docker run --rm myapp pwd
```

### Verify PYTHONPATH
```bash
docker run --rm myapp python -c "import sys; print(sys.path)"
```

### Test Import Resolution
```bash
docker run --rm myapp python -c "from app.utils import helper_function; print('Import successful')"
```

### Debug Module Loading
```bash
docker run -it --rm myapp python
>>> import sys
>>> print(sys.path)
>>> import app.main  # Test if module loads
```

## Summary

Relative import failures in Docker containers are common but solvable. The key is understanding that containers have different execution contexts than your local development environment. By setting proper working directories, configuring PYTHONPATH, and using module execution instead of direct script running, you can ensure your Python applications work consistently across development and production environments.