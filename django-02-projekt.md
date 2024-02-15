# Django - projekt Airline

### Tvorba projektu

```
django-admin startproject airline
```

### První aplikace (Flights) v projektu

```
python manage.py startapp flights
```

V souboru `airline\settings.py`

```python
INSTALLED_APPS = [
    'flights', # doplníme název aplikace
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```


V souboru `airline\urls.py`

```python

urlpatterns = [
    path('admin/', admin.site.urls),
    path('flights/', include('flights.urls')),
]
```
