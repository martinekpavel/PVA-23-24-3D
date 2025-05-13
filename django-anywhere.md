# Deploy

Prerequisite:

- nainstalovaný a nakonfigurovaný git

## PC -> Git

Potřebujeme soubor .gitignore nakonfigurovaný pro python. Ze školních důvodů budeme kopírovat i databázi (nedoporušuji v produkci), tzn. z gitignore vyřadím sqlite.db (Django stuff).
https://github.com/github/gitignore/blob/main/Python.gitignore

```
git init
git add *
git commit -m "first commit"
git branch -M main
```

## Git -> Github

Vytvoř repozitář na githubu (pokud nechci řešit autentizaci na pythonanywhere, pak jej udělám public) a pak jej propoj se soubory v počítači:

```
git remote add origin https://github.com/martinekpavel/PVA-23-24-3D.git
git push -u origin main
```

Pokud není problém s autentizací, pak máme soubory na githubu.

## Github -> Pythonanywhere (EU!)

pokračuji podle:

https://help.pythonanywhere.com/pages/DeployExistingDjangoProject

- uploading your code to PythonAnywhere
- create virtualenv
- settings up your Web app
- edit your WSGI file

Vyřešte allowed hosts = adresa webovky musí být v uvozovkách.

bacha na lomítka u šablon, musí být "/"

vyřešte statické soubory: https://help.pythonanywhere.com/pages/DjangoStaticFiles
a upravte cestu ke statickým souborů na záložce web

v a konzoli se napíše `python manage.py collectstatic`

že všechno funguje zjistíte tak, že zkusíte admin rozhranní, pokud má ccs styly, je to ok


## Možná pomůže

`settings.py`

```python

from pathlib import Path
import os

BASE_DIR = Path(__file__).resolve().parent.parent # tohle asi v souboru bude

STATIC_URL = '/static/'
STATICFILES_DIRS = (
    os.path.join(BASE_DIR, 'static'), 
)

```

### V nastavení na webu:

Static files:

URL
`/static`

Directory
`/home/%učet%/%projekt%/static`


