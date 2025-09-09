# Django Views and Templates

## Views

Views in Django are Python functions or classes that handle HTTP requests and return HTTP responses. They contain the business logic of your application.

### Function-Based Views

```python
# views.py
from django.shortcuts import render
from django.http import HttpResponse
from .models import Book

def book_list(request):
    """Display all books"""
    books = Book.objects.all()
    return render(request, 'books/book_list.html', {'books': books})

def book_detail(request, book_id):
    """Display a single book"""
    book = Book.objects.get(id=book_id)
    return render(request, 'books/book_detail.html', {'book': book})

def book_create(request):
    """Create a new book"""
    if request.method == 'POST':
        # Process form data
        title = request.POST.get('title')
        author_id = request.POST.get('author')
        # Create book...
        return redirect('book_list')
    return render(request, 'books/book_form.html')
```

### Class-Based Views

Django provides generic class-based views for common patterns:

```python
# views.py
from django.views.generic import ListView, DetailView, CreateView, UpdateView, DeleteView
from django.urls import reverse_lazy
from .models import Book

class BookListView(ListView):
    model = Book
    template_name = 'books/book_list.html'
    context_object_name = 'books'
    paginate_by = 10

class BookDetailView(DetailView):
    model = Book
    template_name = 'books/book_detail.html'

class BookCreateView(CreateView):
    model = Book
    template_name = 'books/book_form.html'
    fields = ['title', 'author', 'publication_date', 'isbn', 'price']
    success_url = reverse_lazy('book_list')

class BookUpdateView(UpdateView):
    model = Book
    template_name = 'books/book_form.html'
    fields = ['title', 'author', 'publication_date', 'isbn', 'price']

class BookDeleteView(DeleteView):
    model = Book
    template_name = 'books/book_confirm_delete.html'
    success_url = reverse_lazy('book_list')
```

## Templates

Templates are HTML files with Django template language for dynamic content.

### Template Structure

```
templates/
├── base.html              # Base template
├── books/
│   ├── book_list.html     # Book list template
│   ├── book_detail.html   # Book detail template
│   └── book_form.html     # Book form template
```

### Base Template

```html
<!-- templates/base.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{% block title %}My Django Site{% endblock %}</title>
    <link rel="stylesheet" href="{% static 'css/style.css' %}">
</head>
<body>
    <header>
        <nav>
            <a href="{% url 'home' %}">Home</a>
            <a href="{% url 'book_list' %}">Books</a>
        </nav>
    </header>

    <main>
        {% block content %}{% endblock %}
    </main>

    <footer>
        <p>&copy; 2024 My Django Site</p>
    </footer>

    <script src="{% static 'js/script.js' %}"></script>
</body>
</html>
```

### Template Inheritance

```html
<!-- templates/books/book_list.html -->
{% extends 'base.html' %}

{% block title %}Book List{% endblock %}

{% block content %}
<h1>Book List</h1>

<div class="book-grid">
    {% for book in books %}
    <div class="book-card">
        <h2><a href="{% url 'book_detail' book.pk %}">{{ book.title }}</a></h2>
        <p>By: {{ book.author }}</p>
        <p>Price: ${{ book.price }}</p>
    </div>
    {% empty %}
    <p>No books available.</p>
    {% endfor %}
</div>

<div class="pagination">
    {% if page_obj.has_previous %}
    <a href="?page={{ page_obj.previous_page_number }}">Previous</a>
    {% endif %}

    <span>Page {{ page_obj.number }} of {{ page_obj.paginator.num_pages }}</span>

    {% if page_obj.has_next %}
    <a href="?page={{ page_obj.next_page_number }}">Next</a>
    {% endif %}
</div>
{% endblock %}
```

## Template Language

### Variables

```html
{{ variable }}
{{ object.attribute }}
{{ list.0 }}
```

### Filters

```html
{{ value|lower }}          <!-- Convert to lowercase -->
{{ value|upper }}          <!-- Convert to uppercase -->
{{ value|truncatewords:30 }} <!-- Truncate to 30 words -->
{{ value|date:"F j, Y" }}  <!-- Format date -->
{{ value|default:"N/A" }}  <!-- Default value -->
```

### Tags

```html
{% if condition %}
    <!-- Content if true -->
{% elif other_condition %}
    <!-- Content if other true -->
{% else %}
    <!-- Content if false -->
{% endif %}

{% for item in items %}
    <!-- Loop content -->
{% empty %}
    <!-- Content if items is empty -->
{% endfor %}

{% include 'template.html' %}  <!-- Include another template -->
{% extends 'base.html' %}      <!-- Extend base template -->
{% block content %}{% endblock %} <!-- Define block -->
```

### Custom Template Tags

```python
# templatetags/custom_tags.py
from django import template

register = template.Library()

@register.filter
def currency(value):
    return f"${value:.2f}"

@register.simple_tag
def current_time(format_string):
    from datetime import datetime
    return datetime.now().strftime(format_string)
```

Usage in templates:

```html
{{ price|currency }}
{% current_time "%Y-%m-%d %H:%M:%S" %}
```

## Static Files

Store CSS, JavaScript, and images in the `static` directory:

```
static/
├── css/
│   └── style.css
├── js/
│   └── script.js
└── images/
    └── logo.png
```

In templates:

```html
<link rel="stylesheet" href="{% static 'css/style.css' %}">
<script src="{% static 'js/script.js' %}"></script>
<img src="{% static 'images/logo.png' %}" alt="Logo">
```

## Context Processors

Add common data to all templates:

```python
# settings.py
TEMPLATES = [
    {
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
                'myapp.context_processors.custom_context',
            ],
        },
    },
]

# context_processors.py
def custom_context(request):
    return {
        'site_name': 'My Django Site',
        'current_year': datetime.now().year,
    }
```

## Best Practices

- Use template inheritance for consistent layouts
- Keep business logic in views, not templates
- Use descriptive variable names in context
- Minimize database queries in templates
- Use static files for assets
- Consider using CSS frameworks like Bootstrap
- Keep templates simple and readable
- Use template tags for complex logic