# 🐳 Managing docker-compose.override.yml Across Environments

## Overview

When working with Docker Compose, you may encounter multiple configuration files such as docker-compose.yml and docker-compose.override.yml.
Understanding how these files interact is key to managing your development and production environments cleanly.

## ⚙️ How docker-compose.override.yml Works

- Docker Compose automatically loads docker-compose.override.yml if it exists in the same directory.
- The contents of the override file are merged with the main docker-compose.yml.
- The override file is typically used to define development-specific configurations, such as exposed ports or mounted volumes.

### Example:

```yaml title="docker-compose.yml"
services:
  db:
    image: postgres:15
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: pass
```

```yaml title="docker-compose.override.yml"
services:
  db:
    ports:
      - "5432:5432"
```

When Compose runs, it automatically merges these two files.

## 🏗️ Managing Different Environments

There are several ways to handle your Docker setup across development and production.

### Option 1: Exclude the override file (Simplest)

For production deployments, you can simply remove or rename the override file:

```bash
# Temporarily disable the override file
mv docker-compose.override.yml docker-compose.override.yml.bak

# Or permanently delete it
rm docker-compose.override.yml
```

This ensures only the base configuration is used in production.

### Option 2: Use Environment-Specific Override Files

A cleaner approach is to create dedicated override files for each environment.

```
docker-compose.prod.yml    # Production overrides (no port exposure)
docker-compose.dev.yml     # Development overrides (with ports and volumes)
```

Then start your environment with explicit file references:

```bash
# Development
docker-compose -f docker-compose.yml -f docker-compose.dev.yml up

# Production
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up
```

Example production override file:

```yaml title="docker-compose.prod.yml"
services:
  db:
    ports: []  # Disable exposed ports for security
```

### Option 3: Use Docker Compose Profiles

You can define profiles directly inside docker-compose.yml to toggle services or configurations dynamically.

```yaml title="docker-compose.yml"
services:
  db:
    image: postgres:15
    ports:
      - "5432:5432"
    profiles: ["dev"]
```

Then run with:

```bash
# Development (includes db ports)
docker-compose --profile dev up

# Production (omits dev services)
docker-compose up
```

## ✅ Recommended Workflow

The simplest approach is:

- Add port mappings directly to your docker-compose.yml
- Document this configuration in your project's README.md.

When preparing for production:

- Either remove the ports section, or
- Create a `docker-compose.prod.yml` file with production-safe overrides.

## 🧩 Example Development Setup

```yaml title="docker-compose.yml"
services:
  db:
    image: postgres:15
    environment:
      POSTGRES_USER: devuser
      POSTGRES_PASSWORD: devpass
    ports:
      - "5432:5432"   # Expose port for local development (VS Code, pgAdmin)
```

Later, when deploying:

```yaml title="docker-compose.prod.yml"
services:
  db:
    ports: []  # Remove exposed ports in production
```
