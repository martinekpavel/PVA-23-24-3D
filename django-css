# Django - CSS

### Vytvořím správné složky ve složce aplikace 

V případě, že mám aplikaci newyear, pak ve složce aplikace vytvořím složku `static` a v ní složku s názvem aplikace, v tomto případě `newyear` a v ní bude soubor s kaskádovými styly například: `styles.css`.

Pak do šablony (v mém případě to bude index.html) dopíšu na první řádek: 

```html
{% load static %} 
```

a na správné místo v html kódu vložím:  

```html
<link rel="stylesheet" href="{% static 'newyear/styles.css' %}">
```
