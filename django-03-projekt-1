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
  

    
