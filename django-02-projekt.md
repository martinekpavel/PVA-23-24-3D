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
from django.contrib import admin
from django.urls import path, include

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


    class Passenger(models.Model):
        first = models.CharField(max_length=64)
        last = models.CharField(max_length=64)
        flights = models.ManyToManyField(Flight, blank=True, related_name="passengers")
    
        def __str__(self):
            return f"{self.first} {self.last}"    
```

Další typy modelů (datových typu jednotlivých polí v tabulce) naleznete v [dokumentaci Djanga](https://docs.djangoproject.com/en/5.0/ref/models/fields/).

Vytvoříte soubor pro aplikaci `flights\urls.py`

```python
from django.urls import path 

from . import views

urlpatterns = [
    path("", views.index, name="index")
]
```

Upravíte soubor pro aplikaci `flights\views.py` (logika aplikace, soubor funkcí, které renderují výstupy pro šablony)

```python
from .models import Flight

def index(request):
    return render(request, "flights/index.html", {
        "flights": Flight.objects.all()
    })
```
Vytvoříte správné šablony (layout.html a index.html) např. podle [django-templates](django-templates.md).

Připravíme a vytvoříme databázi (v cmd.exe)

```
python manage.py makemigrations
```

```
python manage.py migrate
```

Vytvoříte superuživatele (zvolíte uživatelské jméno a heslo) pomocí příkazu:

```
python manage.py createsuperuser
```
Výstup může vypadat takto:

```
(virtual-django) C:\airline>python manage.py createsuperuser
Username (leave blank to use 'martinek.p'): admin
Email address:
Password:
Password (again):
Superuser created successfully.
```

Upravíme soubor `admin.py` v aplikaci:

```
from .models import Airport, Flight

admin.site.register(Airport)
admin.site.register(Flight)
```
A nyní můžeme přímo editovat databázi v admin rozhraní aplikace.


