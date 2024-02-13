# Django - projekt Airline

### Tvorba projektu

```
django-admin startproject airline
```

### První aplikace (Flights) v projektu

```
python manage.py startapp flights
```


V souboru `airline\urls.py`

```python

urlpatterns = [
    path('admin/', admin.site.urls),
    path('flights/', include('flights.urls')),
]
```
