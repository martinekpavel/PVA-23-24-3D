# Django - first app (hello)

### Tvorba projektu

```
django-admin startproject lecture3
```

### První aplikace (hello) v projektu

```
python manage.py startapp hello
```

V souboru `lecture3\settings.py`

```python
INSTALLED_APPS = [
    'hello', # doplníme název aplikace
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

V souboru `lecture3\urls.py`

```python
from django.contrib import admin
from django.urls import path, include # bacha na to

urlpatterns = [
    path('admin/', admin.site.urls),
    path('hello/', include('hello.urls')),
]
```

Vytvoříte soubor pro aplikaci `hello\urls.py`

```python
from django.urls import path 

from . import views

urlpatterns = [
    path("", views.index, name="index")
]
```

Upravíte soubor pro aplikaci `hello\views.py` (logika aplikace, soubor funkcí, které renderují výstupy pro šablony (později)

```python
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello")
```
