# Django šablony 

Vytvořím složku `templates` v aplikaci.
Ve složce templates vytvořím složku s názvem aplikace např. `aplikace`

Vytvořím soubory `layout.html` a `index.html`

Obsah souboru `layout.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplikace | Title</title>
</head>
<body>
    {% block body %}
    {% endblock %}
</body>
</html>
```
Obsah souboru `index.html`

```html
{% extends "aplikace/layout.html" %}

{% block body %}

   zde bude kód pro danou stránku, která se právě renderuje

{% endblock %}
```

## Použití cyklu v šabloně

```html
    <ul>
        {% for flight in flights %}
            <li>
               Flight {{ flight.id }}: {{ flight.origin }} to {{ flight.destination }}
            </li>
        {% endfor %}
    </ul>
{% endblock %}
```
