# Django - použití shellu

Do shellu se dostanu příkazem `python manage.py shell`

Pokud chci pracovat s modely, použiji:

```python
>>> from flights.models import *
```

Příklady příkazů
```python
jfk = Airport(code="JFK", city="New York")
jfk.save() # objekt (v tomto případě řádek) ukládám do tabulky
```
