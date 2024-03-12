# Ověřování uživatelů

Vytvoříme novou aplikaci users:

```python
python manage.py startapp users
```
Do souboru `settings.py` doplním:

```python
INSTALLED_APPS = [
    'flights',
    'users', # doplníme název aplikace
    'django.contrib.admin',
    ...
]
```

Do souboru `airline\urls.py` doplním:

```python
    path('users/', include('users.urls')),
```

Vytvoříme soubor pro aplikaci `users\urls.py`

```python
from django.urls import path

from . import views

urlpatterns = [
    path("", views.user, name="user"),
    path("login", views.login_view, name="login"),
    path("logout", views.logout_view, name="logout")
]
```

Upravíme soubor `users\views.py`:

```python
from django.contrib.auth import authenticate, login, logout
from django.http import HttpResponse, HttpResponseRedirect
from django.shortcuts import render
from django.urls import reverse

# Create your views here.
def user(request):
    if not request.user.is_authenticated:
        return HttpResponseRedirect(reverse("login"))
    return render(request, "users/user.html")

def login_view(request):
    if request.method == "POST":
        username = request.POST["username"]
        password = request.POST["password"]
        user = authenticate(request, username=username, password=password)
        if user is not None:
            login(request, user)
            return HttpResponseRedirect(reverse("index"))
        else:
            return render(request, "users/login.html", {
                "message": "Invalid credentials."
            })
    else:
        return render(request, "users/login.html")

def logout_view(request):
    logout(request)
    return render(request, "users/login.html", {
        "message": "Logged out."
    })
```

Vytvoříme šablony `users\templates\users\layout.html`, `users\templates\users\login.html`, `users\templates\users\user.html`.

### Login

```html
{% extends "users/layout.html" %}

{% block body %}

    <h1>Log In</h1>

    {% if message %}
        <div>{{ message }}</div>
    {% endif %}

    <form action="{% url 'login' %}" method="post">
        {% csrf_token %}
        <input type="text" name="username" placeholder="Username">
        <input type="password" name="password" placeholder="Password">
        <input type="submit" value="Login">
    </form>
{% endblock %}
```

### User
```html
{% extends "users/layout.html" %}

{% block body %}

    <h1>Welcome, {{ request.user.first_name }}</h1>

    <ul>
        <li>Username: {{ request.user.username }}</li>
        <li>Email: {{ request.user.email }}</li>
    </ul>

    <a href="{% url 'logout' %}">Log Out</a>
{% endblock %}
```
