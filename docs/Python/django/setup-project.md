# Setting Up a Django Project

## Project Structure

When you create a new Django project, you'll get this basic structure:

```
myproject/
├── manage.py          # Command-line utility for administrative tasks
├── myproject/
│   ├── __init__.py    # Python package indicator
│   ├── settings.py    # Project settings and configuration
│   ├── urls.py        # URL declarations for the project
│   ├── asgi.py        # ASGI configuration for async support
│   └── wsgi.py        # WSGI configuration for deployment
```

## Creating a Project

```bash
# Create a new Django project
django-admin startproject myproject

# Navigate to the project directory
cd myproject

# Create a virtual environment (recommended)
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install Django
pip install django

# Run the development server
python manage.py runserver
```

## Creating an App

Django projects are composed of apps. Each app handles a specific functionality.

```bash
# Create a new app
python manage.py startapp myapp

# This creates:
myapp/
├── __init__.py
├── admin.py       # Admin interface configuration
├── apps.py        # App configuration
├── models.py      # Data models
├── tests.py       # Unit tests
└── views.py       # Business logic
├── migrations/    # Database migrations
│   └── __init__.py
```

## Settings Configuration

The `settings.py` file contains important configuration:

```python
# settings.py
DEBUG = True  # Set to False in production

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'myapp',  # Add your app here
]

SECRET_KEY = 'your-secret-key-here'
```

## Basic Commands

```bash
# Run development server
python manage.py runserver

# Create database tables
python manage.py migrate

# Create a superuser for admin
python manage.py createsuperuser

# Collect static files
python manage.py collectstatic
```

## Development Workflow

1. Create project: `django-admin startproject projectname`
2. Create app: `python manage.py startapp appname`
3. Add app to `INSTALLED_APPS` in settings.py
4. Define models in `models.py`
5. Create migrations: `python manage.py makemigrations`
6. Apply migrations: `python manage.py migrate`
7. Create views and templates
8. Configure URLs
9. Test your application

## Best Practices

- Always use virtual environments
- Keep sensitive information in environment variables
- Use version control (Git)
- Follow Django's naming conventions
- Write tests for your code