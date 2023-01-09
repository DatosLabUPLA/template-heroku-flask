# Template Heroku Flask
Template para repositorios Flask para heroku

## Preparar el proyecto para Heroku
1) Instalar Flask en el entorno virtual
`pip install flask`

2) Instalar Gunicorn en el entorno virtual
`pip install gunicorn`

3) Crear archivo `requirements.txt` con las dependencias del proyecto
`pip freeze > requirements.txt`

4) Crear archivo Procfile con el comando para ejecutar la aplicación
`web: gunicorn wsgi:app`

5) Crear archivo `runtime.txt` con la version de python. Ínformación de las versiones disponibles: https://devcenter.heroku.com/articles/python-support#supported-runtimes
`python-3.10.9`

6) Crear archivo `wsgi.py` con el siguiente contenido
```
from app.main import app
 
if __name__ == "__main__":
        app.run()
```

7) Crear archivo `app/main.py` con el siguiente contenido
```
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<p>Hello, World!</p>"
```

## Heroku
1) Crear nueva app
2) Conectar con el repositorio de GitHub
3) Activar la opción de `Automatic deploys` para que cada vez que se haga un push a la rama `main` se despliegue automáticamente
4) Hacer push a la rama `main` para desplegar la aplicación

## Crear URL
1) Ir a la pestaña `Settings`
2) Ir a la sección `Domains`
3) Crear un nuevo dominio
4) Copiar la URL de la aplicación
5) Ir a Cloudflare
6) Seleccionar el dominio a usar
7) Ir a la pestaña `DNS`
8) Crear un nuevo registro `CNAME` con el nombre del dominio y la URL de la aplicación de Heroku

## Configurar variables de entorno
1) Ir a la pestaña `Settings` en Heroku
2) Ir a la sección `Config Vars`
3) Crear las variables de entorno necesarias

|Variable|Contenido|Descripción|
|---|---|---|
|DEBUG|True|Booleano `True` o `False` determina si la aplicación se ejecuta en modo debug o no