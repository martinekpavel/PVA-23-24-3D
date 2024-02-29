# Pokračování projektu Airline

Do souboru `flights\urls.py` doplním:

```python
path("<int:flight_id>", views.flight, name="flight"),
```

Do souboru `flights\views.py` doplním:

```python
def flight(request, flight_id):
    flight = Flight.objects.get(pk=flight_id)
    return render(request, "flights/flight.html", {
          "flight": flight
    })
```

### Chci zobrazit pasažéry na webu

Do souboru `flights\views.py` do funkce `flight`, do dat pro šablonu přidám:

```python
"passengers": flight.passengers.all()
```

a do šablony doplním:

```python
 <h2>Passengers</h2>
    {% for p in passengers %}
        <li>{{p.first}} {{p.last}}</li>
    {% empty %}
        No passengers.
    {% endfor %}
```
Vytvořím odkaz na seznam letů

```python
<a href="{% url 'index' %}">Back to Flight List</a>
```
   
    
