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

Upravím šablonu daného letu tak, abych tam měl formulář pro přidání pasažéra

```html
<h2>Add Passenger</h2>
    <form action="{% url 'book' flight.id %}" method="POST">
        {% csrf_token %}
        <select name="passenger" id="passenger">
            {% for passanger in non_passengers  %}
            <option value="{{ passanger.id }}">{{ passanger }}</option>
            {% endfor %}
        </select>
        <input type="submit" value="Add Passenger">
    </form>
```

Do funkce `flight` doplním proměnou, která do šablony odešle data těch pasažérů, kteří na daném letu nejsou:

```python
    "non_passengers": Passenger.objects.exclude(flights=flight).all()
```

### Mohu si upravit zobrazení v admin rozhraní 

V souboru  `models.py` provedu úpravy

```python
class FlightAdmin(admin.ModelAdmin):
    list_display = ("id", "origin", "destination", "duration")

class PassengerAdmin(admin.ModelAdmin):
    filter_horizontal = ("flights",)

admin.site.register(Flight, FlightAdmin)
admin.site.register(Passenger, PassengerAdmin)
```

