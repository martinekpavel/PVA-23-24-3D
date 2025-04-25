# Registrace uživatele 

Upravíme `ursl.py` projektu:

```python
path('accounts/', include('django.contrib.auth.urls')),
```

Vytvoříme soubor s formulářem v rámci naší aplikace: `formular.py`


```python
from django import forms 
from django.contrib.auth.forms import UserCreationForm
from django.contrib.auth.models import User

class RegistrationForm(UserCreationForm):
    email = forms.EmailField(required=True)

    class Meta:
        model = User
        fields = ["username", "email", "password1", "password2"]
```
