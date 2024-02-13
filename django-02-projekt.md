### Nový projekt 

```
django-admin startproject airline
```

Nová apka

```
python manage.py startapp flights
```


```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('flights/', include('flights.urls')),
]

```
