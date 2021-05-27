# Api con autenticación oauth2 integrada en Swagger
Este proyecto te permite interactuar con algunos endpoints utilizando el estándar de autorización oauth2.

## Getting Started

Estas instrucciones le proporcionarán una copia del proyecto en funcionamiento en su máquina local con fines de desarrollo y prueba.

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

luego, cree un entorno virtual para el proyecto, puede usar virtualenvwrapper-win si su sistema operativo es Windows

```
pip install virtualenvwrapper-win
mkvirtualenv <nombre_del_entorno>
```

después de eso, instale los paquetes en requirements.txt para asegurarse de tener todo lo necesario

```
pip install -r requirements.txt
```

finalmente, realice las migraciones correspondientes al modelo

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

Obtén tu token de acceso en el endpoint http://127.0.0.1:8000/o/token/

Nota: Puedes enviar un scope personalizado si deseas que el token solo tenga ciertos permisos. Los permisos que están configurados en la aplicación son los siguientes:
```
OAUTH2_PROVIDER = {
    'OAUTH2_BACKEND_CLASS': 'oauth2_provider.oauth2_backends.JSONOAuthLibCore',
    'SCOPES': {'read': 'Read scope', 'write': 'Write scope', 'groups': 'Access to your groups'}
}
```

Cuando ya tengas tu token de acceso, puedes acceder en tu navegador a localhost:8000/ y acceder a la interfaz de swagger para registrar tu token y hacer las peticiones que desees. 

## Autor

* **John Vega**