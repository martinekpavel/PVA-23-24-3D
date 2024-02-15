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

Vytvoříme strukturu tabulek v databázi. V souboru aplikace `flights\models.py`

```python
class Airport(models.Model):
    code = models.CharField(max_length=3)
    city = models.CharField(max_length=64)

    def __str__(self):
        return f"{self.city} ({self.code})"
    
class Flight(models.Model):
    origin = models.ForeignKey(Airport, on_delete=models.CASCADE, related_name="departures")
    destination = models.ForeignKey(Airport, on_delete=models.CASCADE, related_name="arrivals")
    duration = models.IntegerField()

    def __str__(self):
        return f"{self.id}: {self.origin} -> {self.destination} ({self.duration})"
    
```

Přípravíme a vytvoříme databázi (v cmd.exe)

```
python manage.py makemigrations
```

```
python manage.py migrate
```
