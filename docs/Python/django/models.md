# Django Models and Database

## What are Models?

Models in Django are Python classes that define the structure of your database tables. Each model represents a database table, and each attribute represents a database field.

## Creating Models

```python
# models.py
from django.db import models

class Author(models.Model):
    first_name = models.CharField(max_length=100)
    last_name = models.CharField(max_length=100)
    email = models.EmailField()
    birth_date = models.DateField(null=True, blank=True)

    def __str__(self):
        return f"{self.first_name} {self.last_name}"

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE)
    publication_date = models.DateField()
    isbn = models.CharField(max_length=13, unique=True)
    price = models.DecimalField(max_digits=10, decimal_places=2)

    def __str__(self):
        return self.title
```

## Field Types

Django provides many built-in field types:

- `CharField` - For short text
- `TextField` - For long text
- `IntegerField` - For integers
- `DecimalField` - For decimal numbers
- `DateField` / `DateTimeField` - For dates and times
- `EmailField` - For email addresses
- `URLField` - For URLs
- `BooleanField` - For true/false values
- `ForeignKey` - For relationships
- `ManyToManyField` - For many-to-many relationships
- `OneToOneField` - For one-to-one relationships

## Field Options

Common field options:

- `max_length` - Maximum length for CharField
- `null=True` - Allow NULL values in database
- `blank=True` - Allow empty values in forms
- `default` - Default value
- `unique=True` - Ensure unique values
- `choices` - Limit choices to specific values

```python
class Book(models.Model):
    GENRE_CHOICES = [
        ('FICTION', 'Fiction'),
        ('NONFICTION', 'Non-Fiction'),
        ('SCIENCE', 'Science'),
        ('HISTORY', 'History'),
    ]

    title = models.CharField(max_length=200)
    genre = models.CharField(max_length=20, choices=GENRE_CHOICES)
    is_available = models.BooleanField(default=True)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
```

## Relationships

### Foreign Key (One-to-Many)

```python
class Author(models.Model):
    name = models.CharField(max_length=100)

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE)
```

### One-to-One

```python
class User(models.Model):
    username = models.CharField(max_length=100)

class Profile(models.Model):
    user = models.OneToOneField(User, on_delete=models.CASCADE)
    bio = models.TextField()
```

### Many-to-Many

```python
class Tag(models.Model):
    name = models.CharField(max_length=50)

class Article(models.Model):
    title = models.CharField(max_length=200)
    tags = models.ManyToManyField(Tag)
```

## Migrations

After creating or modifying models, you need to create and apply migrations:

```bash
# Create migration files
python manage.py makemigrations

# Apply migrations to database
python manage.py migrate

# View SQL that will be executed
python manage.py sqlmigrate app_name migration_number
```

## Model Methods

Add custom methods to your models:

```python
class Book(models.Model):
    title = models.CharField(max_length=200)
    price = models.DecimalField(max_digits=10, decimal_places=2)

    def __str__(self):
        return self.title

    def get_discounted_price(self, discount=0.1):
        return self.price * (1 - discount)

    @property
    def is_expensive(self):
        return self.price > 50
```

## Model Managers

Custom managers for complex queries:

```python
class BookManager(models.Manager):
    def expensive_books(self):
        return self.filter(price__gt=50)

    def by_author(self, author_name):
        return self.filter(author__name__icontains=author_name)

class Book(models.Model):
    title = models.CharField(max_length=200)
    price = models.DecimalField(max_digits=10, decimal_places=2)
    author = models.ForeignKey(Author, on_delete=models.CASCADE)

    objects = BookManager()
```

## Meta Class

Configure model behavior:

```python
class Book(models.Model):
    title = models.CharField(max_length=200)
    publication_date = models.DateField()

    class Meta:
        ordering = ['-publication_date']  # Order by newest first
        verbose_name = 'Book'
        verbose_name_plural = 'Books'
        unique_together = ['title', 'publication_date']
```

## Querying Models

```python
# Get all books
books = Book.objects.all()

# Filter books
fiction_books = Book.objects.filter(genre='FICTION')
expensive_books = Book.objects.filter(price__gt=50)

# Get single object
book = Book.objects.get(id=1)

# Create new object
new_book = Book.objects.create(title="New Book", price=29.99)

# Update object
book.price = 39.99
book.save()

# Delete object
book.delete()
```

## Best Practices

- Use descriptive field names
- Add `__str__` methods for better representation
- Use appropriate field types
- Set up proper relationships
- Add validation in forms, not just models
- Use migrations for schema changes
- Consider database performance with select_related and prefetch_related