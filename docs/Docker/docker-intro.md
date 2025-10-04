# 🐳 Docker Introduction

## What is Docker?
Docker is an open-source platform that enables developers to build, ship, and run applications inside lightweight, portable containers. Containers package software with all its dependencies, ensuring it runs consistently across different environments—from development to production.

### Why Docker?
- **Consistency**: Eliminates "works on my machine" issues.
- **Isolation**: Each container runs in its own environment.
- **Efficiency**: Shares the host OS kernel, making containers lightweight compared to VMs.
- **Scalability**: Easy to deploy and scale applications.

## Core Concepts

### Images vs Containers
Docker images and containers are often confused, but they serve different purposes:

#### Docker Image
- A read-only template containing the application code, runtime, libraries, and dependencies.
- Acts as a blueprint for creating containers.
- Stored in registries like Docker Hub for sharing and reuse.

#### Docker Container
- A runnable instance of an image.
- Includes a writable layer on top of the image for runtime changes.
- Isolated processes running on the host machine.

### Dockerfile
A Dockerfile is a text file containing instructions to build a Docker image. It defines the base image, copies files, installs dependencies, and sets up the environment.

**Example Dockerfile:**
```dockerfile
# Use Node.js base image
FROM node:14

# Set working directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application code
COPY . .

# Expose port
EXPOSE 3000

# Command to run the app
CMD ["npm", "start"]
```

### Docker Compose
Docker Compose is a tool for defining and running multi-container Docker applications. It uses a `docker-compose.yml` file to configure services, networks, and volumes.

**Example docker-compose.yml:**
```yaml
version: '3.8'
services:
  web:
    build: .
    ports:
      - "3000:3000"
  db:
    image: postgres:13
    environment:
      POSTGRES_PASSWORD: example
```

## Basic Docker Workflow
1. **Write a Dockerfile**: Define how to build your image.
2. **Build the Image**: `docker build -t myapp .`
3. **Run a Container**: `docker run -p 3000:3000 myapp`
4. **Manage Containers**: Use commands like `docker ps`, `docker stop`, `docker rm`

## Key Commands
- `docker build`: Build an image from a Dockerfile
- `docker run`: Create and start a container
- `docker ps`: List running containers
- `docker images`: List available images
- `docker compose up`: Start services defined in docker-compose.yml
- `docker compose down`: Stop and remove containers

## Benefits for Development
- **Rapid Setup**: Spin up development environments quickly
- **Version Control**: Images ensure consistent versions across teams
- **Microservices**: Easy to manage complex applications with multiple services
- **CI/CD Integration**: Streamlines deployment pipelines
