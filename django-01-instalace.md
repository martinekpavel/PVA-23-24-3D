# Django - příprava a instalace

### Virtuální prostředí v Pythonu

Tvoříme příkazem (v prostředí cmd.exe):

```
python -m venv název_virtualního_prostředí
```

Virtuální prostředí se může jmenovat jakkoliv, pokud ho máte ve složce s projektem, může se jmenovat například i `.venv`, pokud je jinde fantazii se meze nekladou. Ale buďte rozumní.

#### Tvorba a spuštění virtuálního prostředí (příklad)

Opět v cmd.exe. Tvořím virtuální prostředí s názvem `dj-venv`.

```
python -m venv dj-venv
```

a spouštím

```
dj-venv\Scripts\activate
```
a vidím název v závorkách, což znamená, že je vše OK. `(dj-venv) C:\`

### Instalace Djanga

V takovém virtuálním prostředí nainstaluji Django.

```
pip install django
```

a jste připraveni vytvořit svůj projekt (webovou aplikaci).
