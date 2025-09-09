# Django URLs and Forms

## URL Configuration

URLs in Django map URL patterns to views. URL configuration is done in `urls.py` files.

### Project URLs

```python
# myproject/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('myapp.urls')),
    path('books/', include('books.urls')),
]
```

### App URLs

```python
# books/urls.py
from django.urls import path
from . import views

app_name = 'books'  # Namespace for URL names

urlpatterns = [
    path('', views.book_list, name='book_list'),
    path('<int:pk>/', views.book_detail, name='book_detail'),
    path('create/', views.book_create, name='book_create'),
    path('<int:pk>/update/', views.book_update, name='book_update'),
    path('<int:pk>/delete/', views.book_delete, name='book_delete'),
]
```

### URL Patterns

- `<int:pk>` - Integer parameter (primary key)
- `<str:slug>` - String parameter
- `<uuid:uuid>` - UUID parameter
- `<path:path>` - String with slashes

### Class-Based View URLs

```python
# books/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.BookListView.as_view(), name='book_list'),
    path('<int:pk>/', views.BookDetailView.as_view(), name='book_detail'),
    path('create/', views.BookCreateView.as_view(), name='book_create'),
    path('<int:pk>/update/', views.BookUpdateView.as_view(), name='book_update'),
    path('<int:pk>/delete/', views.BookDeleteView.as_view(), name='book_delete'),
]
```

## Forms

Django forms handle user input validation and rendering.

### Model Forms

```python
# forms.py
from django import forms
from .models import Book, Author

class BookForm(forms.ModelForm):
    class Meta:
        model = Book
        fields = ['title', 'author', 'publication_date', 'isbn', 'price']
        widgets = {
            'publication_date': forms.DateInput(attrs={'type': 'date'}),
            'price': forms.NumberInput(attrs={'step': '0.01'}),
        }
        labels = {
            'isbn': 'ISBN',
            'publication_date': 'Publication Date',
        }

    def clean_isbn(self):
        isbn = self.cleaned_data.get('isbn')
        if len(isbn) != 13:
            raise forms.ValidationError("ISBN must be 13 characters long")
        return isbn

class AuthorForm(forms.ModelForm):
    class Meta:
        model = Author
        fields = '__all__'  # Include all fields

    def clean_email(self):
        email = self.cleaned_data.get('email')
        if Author.objects.filter(email=email).exists():
            raise forms.ValidationError("This email is already in use")
        return email
```

### Regular Forms

```python
# forms.py
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField(max_length=100, required=True)
    email = forms.EmailField(required=True)
    subject = forms.CharField(max_length=200)
    message = forms.CharField(widget=forms.Textarea, required=True)

    def clean_email(self):
        email = self.cleaned_data.get('email')
        if not email.endswith('@example.com'):
            raise forms.ValidationError("Email must be from example.com domain")
        return email
```

### Form Widgets

```python
# forms.py
from django import forms

class AdvancedForm(forms.Form):
    name = forms.CharField(
        widget=forms.TextInput(attrs={'class': 'form-control', 'placeholder': 'Enter name'})
    )
    email = forms.EmailField(
        widget=forms.EmailInput(attrs={'class': 'form-control'})
    )
    message = forms.CharField(
        widget=forms.Textarea(attrs={'rows': 5, 'cols': 50})
    )
    newsletter = forms.BooleanField(
        required=False,
        widget=forms.CheckboxInput(attrs={'class': 'form-check-input'})
    )
    category = forms.ChoiceField(
        choices=[('general', 'General'), ('support', 'Support'), ('sales', 'Sales')],
        widget=forms.Select(attrs={'class': 'form-select'})
    )
    priority = forms.ChoiceField(
        choices=[('low', 'Low'), ('medium', 'Medium'), ('high', 'High')],
        widget=forms.RadioSelect
    )
```

## Using Forms in Views

### Function-Based Views

```python
# views.py
from django.shortcuts import render, redirect
from .forms import BookForm

def book_create(request):
    if request.method == 'POST':
        form = BookForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect('book_list')
    else:
        form = BookForm()
    return render(request, 'books/book_form.html', {'form': form})

def book_update(request, pk):
    book = Book.objects.get(pk=pk)
    if request.method == 'POST':
        form = BookForm(request.POST, instance=book)
        if form.is_valid():
            form.save()
            return redirect('book_detail', pk=book.pk)
    else:
        form = BookForm(instance=book)
    return render(request, 'books/book_form.html', {'form': form})
```

### Class-Based Views

```python
# views.py
from django.views.generic.edit import CreateView, UpdateView
from .forms import BookForm
from .models import Book

class BookCreateView(CreateView):
    model = Book
    form_class = BookForm
    template_name = 'books/book_form.html'
    success_url = '/books/'

class BookUpdateView(UpdateView):
    model = Book
    form_class = BookForm
    template_name = 'books/book_form.html'
    success_url = '/books/'
```

## Form Rendering in Templates

```html
<!-- templates/books/book_form.html -->
{% extends 'base.html' %}

{% block content %}
<h1>{% if form.instance.pk %}Update{% else %}Create{% endif %} Book</h1>

<form method="post">
    {% csrf_token %}

    <!-- Render all fields -->
    {{ form.as_p }}

    <!-- Or render fields individually -->
    <div>
        {{ form.title.label_tag }}
        {{ form.title }}
        {% if form.title.errors %}
            <div class="error">{{ form.title.errors }}</div>
        {% endif %}
    </div>

    <div>
        {{ form.author.label_tag }}
        {{ form.author }}
        {% if form.author.errors %}
            <div class="error">{{ form.author.errors }}</div>
        {% endif %}
    </div>

    <!-- Non-field errors -->
    {% if form.non_field_errors %}
        <div class="error">{{ form.non_field_errors }}</div>
    {% endif %}

    <button type="submit">Save</button>
</form>
{% endblock %}
```

## Formsets

For handling multiple forms:

```python
# forms.py
from django.forms import modelformset_factory

BookFormSet = modelformset_factory(Book, fields=['title', 'price'], extra=2)

# views.py
def manage_books(request):
    BookFormSet = modelformset_factory(Book, fields=['title', 'price'], extra=2)
    if request.method == 'POST':
        formset = BookFormSet(request.POST)
        if formset.is_valid():
            formset.save()
            return redirect('book_list')
    else:
        formset = BookFormSet()
    return render(request, 'books/manage_books.html', {'formset': formset})
```

## File Upload Forms

```python
# forms.py
from django import forms

class BookWithCoverForm(forms.ModelForm):
    class Meta:
        model = Book
        fields = ['title', 'author', 'cover_image']

    cover_image = forms.ImageField(required=False)

# views.py
def upload_book(request):
    if request.method == 'POST':
        form = BookWithCoverForm(request.POST, request.FILES)
        if form.is_valid():
            form.save()
            return redirect('book_list')
    else:
        form = BookWithCoverForm()
    return render(request, 'books/upload_book.html', {'form': form})
```

## Best Practices

- Always validate form data
- Use `{% csrf_token %}` in templates
- Handle both GET and POST requests
- Provide meaningful error messages
- Use appropriate widgets for better UX
- Consider form validation on both client and server side
- Use formsets for bulk operations
- Keep forms simple and focused