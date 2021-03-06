# Api con autenticación oauth2 integrada en Swagger
Este proyecto te permite interactuar con algunos endpoints utilizando el estándar de autorización oauth2.

## Previsualización

Si quieres echar un vistazo a la api antes de clonar el proyecto, puedes dirigirte a: https://oauth2-authentication-1504.herokuapp.com/.
Utiliza las siguientes credenciales de prueba para obtener un token de acceso (Puedes utilizar postman):

```
{
    "grant_type": "password",
    "username": "root",
    "password": "root",
    "client_id": "MC9vL2hbrrjqeGAzANgSYoLSFjaBrRni8xeHzeOZ",
    "client_secret": "eswjWtLw8irrDrCHebKKSgiUOSQb851q6dZQ5UqiSUYQPciOQRxjKi5YG652OGa4yDnzS3otGIFHupUZP2Bewm5ALQHF392ph6jl1j9dgB0DlBBUyRCJRQn6aWa5xe9Q"
}
```
Recuerda anteponer la palabra "bearer" a tu token:

![image](https://user-images.githubusercontent.com/71096926/121090434-360d2480-c7ae-11eb-9441-575c6de79611.png)

## Guía rápida

Estas instrucciones te proporcionarán una copia del proyecto en funcionamiento en tu máquina local con fines de desarrollo y prueba.

### Prerrequisito

Si quieres probar, necesitarás estos requisitos previos

```
Python > 3.6
```

### Instalación

Primero, clona el proyecto en tu computadora

```
git clone https://github.com/johnLee1501/oauth2_authentication.git
```

luego, crea un entorno virtual para el proyecto, puede usar virtualenvwrapper-win si tu sistema operativo es Windows

```
pip install virtualenvwrapper-win
mkvirtualenv <nombre_del_entorno>
```

después de eso, instala los paquetes de requirements.txt para asegurarte de tener todo lo necesario

```
pip install -r requirements.txt
```

finalmente, realiza las migraciones correspondientes al modelo

```
py manage.py makemigrations
py manage.py migrate
```

Listo! ya puedes ejecutarlo

```
py manage.py runserver
```

Crea un superusuario

```
py manage.py createsuperuser
```

Ingresa a localhost:8000/admin para registrar tu aplicación cliente. No olvides anotar tu client_id y client_secret
```
Client type: Confidential
Authorization grant type: Resource owner password-based
```

![image](https://user-images.githubusercontent.com/71096926/119763670-924e7b00-be75-11eb-8e77-b7f8a8cfbde5.png)

Obtén tu token de acceso en el endpoint http://127.0.0.1:8000/o/token/ , puedes utilizar postman para mayor comodidad.

![image](https://user-images.githubusercontent.com/71096926/119763793-ce81db80-be75-11eb-9947-2f4143dce1e8.png)

![image](https://user-images.githubusercontent.com/71096926/119763932-17d22b00-be76-11eb-83a1-d6235dc5be9e.png)

Nota: Puedes enviar un scope personalizado si deseas que el token solo tenga ciertos permisos. Los permisos que están configurados en la aplicación son los siguientes:
```
OAUTH2_PROVIDER = {
    'OAUTH2_BACKEND_CLASS': 'oauth2_provider.oauth2_backends.JSONOAuthLibCore',
    'SCOPES': {'read': 'Read scope', 'write': 'Write scope', 'groups': 'Access to your groups'}
}
```

Cuando ya tengas tu token de acceso, puedes acceder en tu navegador a localhost:8000/ y acceder a la interfaz de swagger para registrar tu token y hacer las peticiones que desees. 

![image](https://user-images.githubusercontent.com/71096926/119764123-78616800-be76-11eb-8448-c8944009ce95.png)

![image](https://user-images.githubusercontent.com/71096926/119764187-93cc7300-be76-11eb-8903-cd64d60b8f7c.png)

El endpoint get groups solo puede ser utilizado si el token tiene el scope "groups"

## Autor

* **John Vega**

Para mayor información puedes leer la documentación de Django OAuth Toolkit
https://django-oauth-toolkit.readthedocs.io/en/latest/rest-framework/rest-framework.html
