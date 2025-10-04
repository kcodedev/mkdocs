# Docker Container Interaction

This guide covers how to run commands inside running Docker containers, access interactive shells, and interact with containers for debugging and maintenance purposes.

## Running Commands in Containers

Use `docker exec` to execute commands in already running containers without stopping them.

### Basic Syntax
```bash
docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
```

Common options:
- `-i`: Keep STDIN open even if not attached
- `-t`: Allocate a pseudo-TTY
- `-it`: Interactive terminal (most common for shells)

### Examples

#### PostgreSQL Database Container
```bash
# Access PostgreSQL shell
docker exec -it postgres-db psql -U postgres -d myapp

# Run a SQL query directly
docker exec -it postgres-db psql -U postgres -d myapp -c "SELECT * FROM users LIMIT 5;"

# Check database size
docker exec -it postgres-db psql -U postgres -d myapp -c "SELECT pg_size_pretty(pg_database_size('myapp'));"

# Get a bash shell in the container
docker exec -it postgres-db bash

# Inside the shell, you can run:
psql -U postgres -d myapp
# or
pg_dump -U postgres myapp > backup.sql
```

#### FastAPI Python Backend Container
```bash
# Get a Python shell
docker exec -it fastapi-app python

# Run a Python script or command
docker exec -it fastapi-app python -c "import app; print('App loaded successfully')"

# Access bash shell
docker exec -it fastapi-app bash

# Inside the shell, common commands:
python main.py
pip list
python -m pytest
curl http://localhost:8000/docs
```

#### React Frontend Container
```bash
# Run npm scripts
docker exec -it react-app npm run build

# Start development server (if not already running)
docker exec -it react-app npm start

# Install new dependencies
docker exec -it react-app npm install axios

# Access bash shell
docker exec -it react-app bash

# Inside the shell, common commands:
npm run test
npm run lint
ls -la /app/src
```

## Interactive Shell Access

### Getting a Shell in Any Container
```bash
# Try bash first (most common)
docker exec -it container_name bash

# If bash not available, try sh
docker exec -it container_name sh

# For Alpine-based images
docker exec -it container_name ash
```

### Persistent Shell Session
```bash
# Start a long-running shell
docker exec -it postgres-db bash

# Now you're inside the container
# Run commands interactively
psql -U postgres
createdb new_database
# Exit with Ctrl+D or 'exit'
```

## Container Inspection and Monitoring

### View Container Logs
```bash
# View last 100 lines
docker logs --tail 100 container_name

# Follow logs in real-time
docker logs -f container_name

# View logs since specific time
docker logs --since "2024-01-01T00:00:00" container_name
```

### Inspect Container Details
```bash
# Get detailed container information
docker inspect container_name

# View environment variables
docker exec container_name env

# Check running processes
docker exec container_name ps aux

# View disk usage
docker exec container_name df -h
```

### Network Inspection
```bash
# Check network connections
docker exec container_name netstat -tlnp

# Test connectivity to other services
docker exec fastapi-app curl http://postgres-db:5432
docker exec react-app curl http://fastapi-app:8000
```

## Debugging Common Issues

### Database Connection Issues
```bash
# Check if PostgreSQL is running
docker exec postgres-db pg_isready -U postgres -d myapp

# View PostgreSQL logs
docker logs postgres-db

# Check database connectivity from FastAPI
docker exec fastapi-app python -c "
import psycopg2
try:
    conn = psycopg2.connect('host=postgres-db user=postgres dbname=myapp')
    print('Database connection successful')
    conn.close()
except Exception as e:
    print(f'Connection failed: {e}')
"
```

### Application Health Checks
```bash
# Test FastAPI endpoints
docker exec fastapi-app curl -f http://localhost:8000/health || echo "Health check failed"

# Check React build
docker exec react-app npm run build && echo "Build successful" || echo "Build failed"

# View application logs
docker logs fastapi-app
docker logs react-app
```

### File System Operations
```bash
# Copy files from container to host
docker cp container_name:/app/logs/error.log ./error.log

# Copy files from host to container
docker cp ./config.json container_name:/app/config.json

# View file permissions
docker exec container_name ls -la /app
```

## Best Practices

1. **Use descriptive container names** for easier interaction
2. **Avoid running privileged containers** unless necessary
3. **Use environment variables** for configuration instead of hardcoding
4. **Monitor resource usage** with `docker stats`
5. **Clean up stopped containers** regularly with `docker container prune`

## Troubleshooting

- **Command not found**: Check if the command is installed in the container image
- **Permission denied**: You might need to run as root with `docker exec -u root -it container_name bash`
- **Container not running**: Use `docker ps` to check running containers
- **Network issues**: Verify container networking with `docker network ls` and `docker network inspect`