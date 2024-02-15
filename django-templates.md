# Django šablony 

Vytvořím složku `templates` v aplikaci.
Ve složce templates vytvořím složku s názvem aplikace např. `flights`

Vytvořím soubory `layout.html` a `index.html`

Obsah souboru `layout.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flights</title>
</head>
<body>
    {% block body %}
    {% endblock %}
</body>
</html>
```
Obsah souboru `index.html`

```html
{% extends "flights/layout.html" %}

{% block body %}

    <h1>Flights</h1>
    <ul>
        {% for flight in flights %}
            <li>
                <a href="{% url 'flight' flight.id %}">
                    Flight {{ flight.id }}: {{ flight.origin }} to {{ flight.destination }}
                </a>
            </li>
        {% endfor %}
    </ul>

{% endblock %}
```
