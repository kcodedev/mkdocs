# Django Authentication and Admin

## User Authentication

Django provides a complete authentication system out of the box.

### User Model

Django comes with a built-in User model:

```python
from django.contrib.auth.models import User

# Create user
user = User.objects.create_user('john', 'john@example.com', 'password123')

# Get user
user = User.objects.get(username='john')

# Check password
user.check_password('password123')  # Returns True/False

# Change password
user.set_password('newpassword')
user.save()
```

### Custom User Model

For more complex user requirements:

```python
# models.py
from django.contrib.auth.models import AbstractUser

class CustomUser(AbstractUser):
    bio = models.TextField(blank=True)
    birth_date = models.DateField(null=True, blank=True)
    profile_picture = models.ImageField(upload_to='profiles/', null=True, blank=True)

    def __str__(self):
        return self.username
```

```python
# settings.py
AUTH_USER_MODEL = 'myapp.CustomUser'
```

## Authentication Views

Django provides built-in authentication views:

```python
# urls.py
from django.contrib.auth import views as auth_views
from django.urls import path

urlpatterns = [
    path('login/', auth_views.LoginView.as_view(template_name='auth/login.html'), name='login'),
    path('logout/', auth_views.LogoutView.as_view(next_page='home'), name='logout'),
    path('password_change/', auth_views.PasswordChangeView.as_view(
        template_name='auth/password_change.html',
        success_url='/password_change/done/'
    ), name='password_change'),
    path('password_change/done/', auth_views.PasswordChangeDoneView.as_view(
        template_name='auth/password_change_done.html'
    ), name='password_change_done'),
]
```

### Custom Login View

```python
# views.py
from django.contrib.auth import authenticate, login
from django.shortcuts import render, redirect

def custom_login(request):
    if request.method == 'POST':
        username = request.POST.get('username')
        password = request.POST.get('password')
        user = authenticate(request, username=username, password=password)
        if user is not None:
            login(request, user)
            return redirect('home')
        else:
            return render(request, 'auth/login.html', {'error': 'Invalid credentials'})
    return render(request, 'auth/login.html')
```

## User Registration

```python
# forms.py
from django.contrib.auth.forms import UserCreationForm
from django.contrib.auth.models import User

class CustomUserCreationForm(UserCreationForm):
    email = forms.EmailField(required=True)

    class Meta:
        model = User
        fields = ('username', 'email', 'password1', 'password2')

    def save(self, commit=True):
        user = super().save(commit=False)
        user.email = self.cleaned_data['email']
        if commit:
            user.save()
        return user
```

```python
# views.py
from django.shortcuts import render, redirect
from .forms import CustomUserCreationForm

def register(request):
    if request.method == 'POST':
        form = CustomUserCreationForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect('login')
    else:
        form = CustomUserCreationForm()
    return render(request, 'auth/register.html', {'form': form})
```

## Protecting Views

### Login Required Decorator

```python
# views.py
from django.contrib.auth.decorators import login_required
from django.shortcuts import render

@login_required
def profile(request):
    return render(request, 'profile.html', {'user': request.user})

@login_required(login_url='/login/')
def dashboard(request):
    return render(request, 'dashboard.html')
```

### Class-Based View Protection

```python
# views.py
from django.contrib.auth.mixins import LoginRequiredMixin
from django.views.generic import TemplateView

class ProfileView(LoginRequiredMixin, TemplateView):
    template_name = 'profile.html'
    login_url = '/login/'

    def get_context_data(self, **kwargs):
        context = super().get_context_data(**kwargs)
        context['user'] = self.request.user
        return context
```

### Permission-Based Access

```python
# views.py
from django.contrib.auth.decorators import permission_required

@permission_required('myapp.can_view_reports', login_url='/login/')
def reports(request):
    return render(request, 'reports.html')
```

## Django Admin

Django provides a powerful admin interface for managing your models.

### Basic Admin Setup

```python
# admin.py
from django.contrib import admin
from .models import Book, Author

@admin.register(Book)
class BookAdmin(admin.ModelAdmin):
    list_display = ('title', 'author', 'publication_date', 'price')
    list_filter = ('publication_date', 'author')
    search_fields = ('title', 'author__name')
    ordering = ('-publication_date',)

@admin.register(Author)
class AuthorAdmin(admin.ModelAdmin):
    list_display = ('first_name', 'last_name', 'email')
    search_fields = ('first_name', 'last_name', 'email')
```

### Advanced Admin Features

```python
# admin.py
from django.contrib import admin
from .models import Book, Author

class BookInline(admin.TabularInline):
    model = Book
    extra = 0
    fields = ('title', 'publication_date', 'price')

@admin.register(Author)
class AuthorAdmin(admin.ModelAdmin):
    list_display = ('first_name', 'last_name', 'email', 'book_count')
    search_fields = ('first_name', 'last_name', 'email')
    inlines = [BookInline]

    def book_count(self, obj):
        return obj.book_set.count()
    book_count.short_description = 'Number of Books'

@admin.register(Book)
class BookAdmin(admin.ModelAdmin):
    list_display = ('title', 'author', 'publication_date', 'price', 'is_recent')
    list_filter = ('publication_date', 'author', 'price')
    search_fields = ('title', 'author__first_name', 'author__last_name')
    ordering = ('-publication_date',)
    date_hierarchy = 'publication_date'
    list_editable = ('price',)
    readonly_fields = ('created_at', 'updated_at')

    fieldsets = (
        ('Basic Information', {
            'fields': ('title', 'author', 'isbn')
        }),
        ('Publication Details', {
            'fields': ('publication_date', 'price'),
            'classes': ('collapse',)
        }),
        ('Timestamps', {
            'fields': ('created_at', 'updated_at'),
            'classes': ('collapse',)
        }),
    )

    def is_recent(self, obj):
        from datetime import datetime, timedelta
        return obj.publication_date > datetime.now().date() - timedelta(days=365)
    is_recent.boolean = True
    is_recent.short_description = 'Recent Publication'
```

### Custom Admin Actions

```python
# admin.py
from django.contrib import admin
from .models import Book

@admin.register(Book)
class BookAdmin(admin.ModelAdmin):
    # ... other admin configuration ...

    actions = ['mark_as_featured', 'unmark_as_featured']

    def mark_as_featured(self, request, queryset):
        queryset.update(is_featured=True)
        self.message_user(request, f'{queryset.count()} books marked as featured.')
    mark_as_featured.short_description = 'Mark selected books as featured'

    def unmark_as_featured(self, request, queryset):
        queryset.update(is_featured=False)
        self.message_user(request, f'{queryset.count()} books unmarked as featured.')
    unmark_as_featured.short_description = 'Unmark selected books as featured'
```

## User Permissions and Groups

### Creating Permissions

```python
# models.py
from django.db import models

class Article(models.Model):
    title = models.CharField(max_length=200)
    content = models.TextField()
    author = models.ForeignKey('auth.User', on_delete=models.CASCADE)
    published = models.BooleanField(default=False)

    class Meta:
        permissions = [
            ('can_publish_articles', 'Can publish articles'),
            ('can_edit_own_articles', 'Can edit own articles'),
            ('can_delete_articles', 'Can delete articles'),
        ]
```

### Using Permissions in Views

```python
# views.py
from django.contrib.auth.decorators import permission_required
from django.core.exceptions import PermissionDenied

@permission_required('myapp.can_publish_articles')
def publish_article(request, article_id):
    article = Article.objects.get(id=article_id)
    article.published = True
    article.save()
    return redirect('article_list')

def edit_article(request, article_id):
    article = Article.objects.get(id=article_id)
    if not (request.user == article.author or request.user.has_perm('myapp.can_edit_articles')):
        raise PermissionDenied
    # Edit logic here
```

### Groups

```python
# Create groups and assign permissions
from django.contrib.auth.models import Group, Permission
from django.contrib.contenttypes.models import ContentType

# Create groups
editors_group, created = Group.objects.get_or_create(name='Editors')
admins_group, created = Group.objects.get_or_create(name='Admins')

# Get permissions
content_type = ContentType.objects.get_for_model(Article)
publish_perm = Permission.objects.get(content_type=content_type, codename='can_publish_articles')
edit_perm = Permission.objects.get(content_type=content_type, codename='can_edit_articles')

# Assign permissions to groups
editors_group.permissions.add(edit_perm)
admins_group.permissions.add(publish_perm, edit_perm)
```

## Best Practices

- Use Django's built-in authentication system
- Implement proper password policies
- Use HTTPS in production
- Implement rate limiting for login attempts
- Use Django's permission system effectively
- Customize the admin interface for better usability
- Log security-related events
- Implement proper session management
- Use social authentication when appropriate
- Regularly update Django for security patches