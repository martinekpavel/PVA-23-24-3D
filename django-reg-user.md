# Registrace uživatele 

Zdroj: https://dev.to/donesrom/how-to-set-up-django-built-in-registration-in-2023-41hg

Vytvoříme soubor s formulářem v rámci naší aplikace: `formular.py`

```python
from django import forms 
from django.contrib.auth.forms import UserCreationForm
from django.contrib.auth.models import User

class RegistrationForm(UserCreationForm):
    email = forms.EmailField(required=True)

    class Meta:
        model = User
        fields = ["username", "first_name", "last_name","email", "password1", "password2"]
```

V souboru aplikace upravíme `views.py`

```python
from . formular import *
from django.shortcuts import render, redirect # přidáme redirect
from django.contrib.auth.forms import *

def sign_up(request):
    if request.method == "POST":
        form = RegistrationForm(request.POST)
        if form.is_valid():
            user = form.save()
            login(request,user)
            return redirect("/")
    else:
        form = RegistrationForm()
    
    return render(request, "users\sign_up.html", {
        "form":form
        })
```

Upravíme `urls.py` aplikace:

```python
path("sign_up", views.sign_up, name="sign_up")
```

Vytvoříme šablonu:  `.\templates\aplikace\sign_up.html`

```python
{% extends "users/layout.html" %}

{% block body %}

<h3>Registrace uživatele</h3>
<form method="post">
    {% csrf_token %}
    {{ form.as_p }}
    <button type="submit">Sign up</button>
</form>

{% endblock %}
```

Chceme-li ve formuláři češtinu upravíme `settings.py`

```python
# LANGUAGE_CODE = 'en-us'
LANGUAGE_CODE = 'cs'
```
