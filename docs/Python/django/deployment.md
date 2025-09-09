# Django Deployment

## Preparing for Production

### Environment Variables

Never hardcode sensitive information in your code:

```python
# settings.py
import os

SECRET_KEY = os.environ.get('DJANGO_SECRET_KEY')
DEBUG = os.environ.get('DJANGO_DEBUG', 'False') == 'True'
ALLOWED_HOSTS = os.environ.get('DJANGO_ALLOWED_HOSTS', '').split(',')

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': os.environ.get('DB_NAME'),
        'USER': os.environ.get('DB_USER'),
        'PASSWORD': os.environ.get('DB_PASSWORD'),
        'HOST': os.environ.get('DB_HOST'),
        'PORT': os.environ.get('DB_PORT'),
    }
}
```

### Production Settings

```python
# settings.py
DEBUG = False
SECRET_KEY = os.environ.get('DJANGO_SECRET_KEY')

ALLOWED_HOSTS = [
    'yourdomain.com',
    'www.yourdomain.com',
    'your-server-ip',
]

# Security settings
SECURE_SSL_REDIRECT = True
SECURE_HSTS_SECONDS = 31536000
SECURE_HSTS_INCLUDE_SUBDOMAINS = True
SECURE_HSTS_PRELOAD = True
SECURE_CONTENT_TYPE_NOSNIFF = True
SECURE_BROWSER_XSS_FILTER = True
SESSION_COOKIE_SECURE = True
CSRF_COOKIE_SECURE = True
X_FRAME_OPTIONS = 'DENY'

# Static files
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'static'),
]

# Media files
MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
```

## Database Setup

### PostgreSQL (Recommended for Production)

```bash
# Install PostgreSQL
sudo apt-get install postgresql postgresql-contrib

# Create database and user
sudo -u postgres psql
CREATE DATABASE myproject;
CREATE USER myuser WITH PASSWORD 'mypassword';
GRANT ALL PRIVILEGES ON DATABASE myproject TO myuser;
\q
```

```python
# settings.py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'myproject',
        'USER': 'myuser',
        'PASSWORD': 'mypassword',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

### MySQL

```bash
# Install MySQL
sudo apt-get install mysql-server
sudo mysql_secure_installation

# Create database
mysql -u root -p
CREATE DATABASE myproject;
CREATE USER 'myuser'@'localhost' IDENTIFIED BY 'mypassword';
GRANT ALL PRIVILEGES ON myproject.* TO 'myuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

```python
# settings.py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'myproject',
        'USER': 'myuser',
        'PASSWORD': 'mypassword',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

## Web Server Setup

### Gunicorn

Gunicorn is a Python WSGI HTTP Server:

```bash
pip install gunicorn
```

Create a systemd service file:

```bash
# /etc/systemd/system/gunicorn.service
[Unit]
Description=gunicorn daemon
After=network.target

[Service]
User=your-user
Group=www-data
WorkingDirectory=/path/to/your/project
ExecStart=/path/to/your/venv/bin/gunicorn --access-logfile - --workers 3 --bind unix:/path/to/your/project.sock myproject.wsgi:application

[Install]
WantedBy=multi-user.target
```

```bash
sudo systemctl start gunicorn
sudo systemctl enable gunicorn
```

### Nginx

Nginx is a web server and reverse proxy:

```bash
sudo apt-get install nginx
```

Create Nginx configuration:

```nginx
# /etc/nginx/sites-available/myproject
server {
    listen 80;
    server_name your-domain.com www.your-domain.com;

    location = /favicon.ico { access_log off; log_not_found off; }

    location /static/ {
        alias /path/to/your/project/staticfiles/;
    }

    location /media/ {
        alias /path/to/your/project/media/;
    }

    location / {
        include proxy_params;
        proxy_pass http://unix:/path/to/your/project.sock;
    }
}
```

```bash
sudo ln -s /etc/nginx/sites-available/myproject /etc/nginx/sites-enabled
sudo nginx -t
sudo systemctl restart nginx
```

## SSL Certificate (Let's Encrypt)

```bash
sudo apt-get install certbot python3-certbot-nginx
sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
```

## Docker Deployment

### Dockerfile

```dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

RUN python manage.py collectstatic --noinput

EXPOSE 8000

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "myproject.wsgi:application"]
```

### docker-compose.yml

```yaml
version: '3.8'

services:
  web:
    build: .
    command: gunicorn myproject.wsgi:application --bind 0.0.0.0:8000
    volumes:
      - .:/app
      - static_volume:/app/staticfiles
    expose:
      - 8000
    environment:
      - DJANGO_SETTINGS_MODULE=myproject.settings.production

  nginx:
    image: nginx:alpine
    ports:
      - "80:80"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
      - static_volume:/app/staticfiles
    depends_on:
      - web

  db:
    image: postgres:13
    environment:
      - POSTGRES_DB=myproject
      - POSTGRES_USER=myuser
      - POSTGRES_PASSWORD=mypassword
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
  static_volume:
```

## Cloud Deployment

### Heroku

1. Install Heroku CLI
2. Create requirements.txt
3. Create Procfile:

```
web: gunicorn myproject.wsgi --log-file -
```

4. Create runtime.txt:

```
python-3.9.7
```

5. Deploy:

```bash
heroku create your-app-name
git push heroku main
heroku run python manage.py migrate
```

### AWS

1. Launch EC2 instance
2. Install required software
3. Configure security groups
4. Set up domain and SSL
5. Deploy your Django application

### DigitalOcean App Platform

1. Connect your repository
2. Configure build and run commands
3. Set environment variables
4. Deploy

## Monitoring and Logging

### Django Logging

```python
# settings.py
LOGGING = {
    'version': 1,
    'disable_existing_loggers': False,
    'formatters': {
        'verbose': {
            'format': '{levelname} {asctime} {module} {process:d} {thread:d} {message}',
            'style': '{',
        },
    },
    'handlers': {
        'file': {
            'level': 'ERROR',
            'class': 'logging.FileHandler',
            'filename': 'django_errors.log',
            'formatter': 'verbose',
        },
    },
    'root': {
        'handlers': ['file'],
        'level': 'WARNING',
    },
}
```

### Monitoring Tools

- **Sentry**: Error tracking and monitoring
- **New Relic**: Application performance monitoring
- **DataDog**: Infrastructure and application monitoring
- **Prometheus + Grafana**: Metrics collection and visualization

## Backup Strategy

### Database Backup

```bash
# PostgreSQL
pg_dump myproject > backup.sql

# MySQL
mysqldump -u myuser -p myproject > backup.sql
```

### File Backup

```bash
# Backup media files
tar -czf media_backup.tar.gz media/

# Backup entire project
tar -czf project_backup.tar.gz /path/to/project/
```

### Automated Backups

Use cron jobs or services like:
- AWS Backup
- DigitalOcean Backups
- Custom scripts with cloud storage

## Performance Optimization

### Database Optimization

```python
# Use select_related for foreign keys
books = Book.objects.select_related('author').all()

# Use prefetch_related for many-to-many
authors = Author.objects.prefetch_related('book_set').all()

# Database indexes
class Book(models.Model):
    title = models.CharField(max_length=200, db_index=True)
    publication_date = models.DateField(db_index=True)
```

### Caching

```python
# settings.py
CACHES = {
    'default': {
        'BACKEND': 'django.core.cache.backends.redis.RedisCache',
        'LOCATION': 'redis://127.0.0.1:6379/',
    }
}

# views.py
from django.views.decorators.cache import cache_page

@cache_page(60 * 15)  # Cache for 15 minutes
def book_list(request):
    # View logic
```

### Static Files Optimization

```python
# settings.py
STATICFILES_STORAGE = 'django.contrib.staticfiles.storage.ManifestStaticFilesStorage'
```

## Security Checklist

- [ ] DEBUG = False in production
- [ ] SECRET_KEY is environment variable
- [ ] ALLOWED_HOSTS properly configured
- [ ] HTTPS enabled
- [ ] SECURE_SSL_REDIRECT = True
- [ ] Database credentials secured
- [ ] File permissions correct
- [ ] Regular security updates
- [ ] Firewall configured
- [ ] SSL certificate valid
- [ ] Backup strategy in place

## Best Practices

- Use environment variables for configuration
- Implement proper logging
- Set up monitoring and alerts
- Regular backups
- Keep dependencies updated
- Use HTTPS everywhere
- Implement rate limiting
- Regular security audits
- Document your deployment process
- Test deployments before going live