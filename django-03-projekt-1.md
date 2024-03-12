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

### Chci mít možnost přidat pasažéry k letu

Měli byste vědět, kam doplníte tento řádek

```python
path("<int:flight_id>/book", views.book, name="book"),
```
Ve správném souboru uděláme následující změny:

```python
from django.http import HttpResponseRedirect
from django.urls import reverse

def book(request, flight_id):
    if request.method == "POST":
        flight = Flight.objects.get(pk=flight_id)
        passenger = Passenger.objects.get(pk=int(request.POST["passenger"]))
        passenger.flights.add(flight)
        return HttpResponseRedirect(reverse("flight", args=(flight.id,)))
```   
    
