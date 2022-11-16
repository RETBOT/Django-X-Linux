# Curso Practico de Django desde Sistemas Operativos GNU Linux
En este repositorio iremos viendo todo lo necesario para la instalacion de los elementos necesarios 


# Instalacion del Sistema Operativo
Para este taller se usara el Sistema operativo Fedora 36
![Fedora-Logo](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/LogoFedora.png)

Por lo que deberemos de ir al siguiente link para obtener la ISO.

<a href="https://getfedora.org/es/workstation/download/">Ir a la pagina de descarga</a>

<div align="center">
<h2> Virtualizacion del sistema operativo </h3>
  </div>
Una vez teniendo la iso, vamos a requerir un virtualizador. Puede ser cualquiera, pero para este caso reduciremos las alternativas a solo 2
<b> VMware Player/Pro(Workstation) o VirtualBox <b>

Links de descarga: 
  <br>
  <b> VMware : <b> https://www.vmware.com/mx/products/workstation-player/workstation-player-evaluation.html 
  <br>
  <b> Virtual Box: <b>https://www.virtualbox.org/ 
    

# Instalacion de las herramientas necesarias en el SO
Instalacion del IDE/Editor Visual Studio Code : 
Descargamos el archivo <b>.rmp</b> del siguiente sitio
<div align="center">
    <a href="https://code.visualstudio.com/download">Ir al sitio oficial de descarga</a>
 </div>
Ir a la carpeta en donde se almaceno el .rpm, regularmente por defecto se va a la carpeta de Descargas. Con el siguiente comando podremos ir a esa carpeta.
  <br>
  
    cd $HOME/Descargas/
Una vez estando ahi ejecutamos el siguiente comando para instalar el editor.
  <br>
  
    sudo rpm -i code-1.73.1-1667967421.el7.x86_64.rpm    
    




Debido a que estamos en GNU/Linux no tendremos que realizar pasos como descargar o actualizar la version de python. Debido a que por defecto
ya viene integrada la version mas reciente o de las mas recientes de python3.
    
 <div align="center">
   <h2> Entorno virtual de python <h2>
 </div>
     
No son sumamente necesarios para el funcionamiento del proyecto, mas sin embargo son <b>altamente recomendados<b> usarlos en entornos 
de produccion. Por lo que en este taller lo manejaremos por entornos virtuales para mejor uso practico.
<div align="center">
  <h4> Comandos necesarios desde la terminal <h4>
    </div>
 Deberemos de hacer una serie de pasos en la terminal antes de ir a la codificacion en Visual Studio Code.
  <b> Creacion de carpetas <b>
  <br>
  
    mkdir congresoDjango
  <b> Cambiar de directorio a la carpeta que creamos <b>
  <br>
  
    cd congresoDjango/
  <br>
  <b> Instalacion de pip <b>
      
    sudo dnf install python3-pip
Verificamos que se haya instalado pip correctamente. 
    <br>
    
    pip --help
Instalacion del entorno de virtual de python
    <br>
    
    pip3 install pipenv
    
# Preparativos para el uso de Django
Una vez hemos conseguido pip y creado nuestra carpeta de trabajo, lo que prosigue es instalar Django con pip con el siguiente comando
<br>
      
    pipenv install django
El siguiente paso sera entrar al <b>pipenv shell<b> para que todos los comandos que escribamos afecten directamente a ese proyecto
    <br>
    
    pipenv shell
Hasta este punto si todo sale bien, te debera de aparecer al lado izquierdo en la terminal algo similar a esto <b>(base)<b>
    <br>
<div align="center">
  <h2> Creacion de proyecto de django </h2>
    </div>
 Hemos llegado a nuestro primer momento de interaccion con django, para comenzar nuestro proyecto introducimos el siguiente comando.
  <br>
    
    django-admin startproject congreso .
    
   Se anade el . al final para que nos genere los archivos en el directorio actual
   Verificamos si se nos han anadido los archivos con el siguiente comando :
    <br>
    
    tree
 Arrancamos el motor de django por primera vez.
    <br>
    
    python manage.py runserver
 <div align="center">
   <h3> Creacion de aplicaciones </h3>
 </div>
Para creacion de aplicaciones en django lo hacemos con el siguiente comando.
    <br>
    
    django-admin startapp blog
<div align="center">
 <h3>Migracion de la base de datos<h3>
 </div>
    <br>
    
    python manage.py migrate
  
 # Creacion de super usuario para la administracion del proyecto
 Lo cremos con el siguiente comando : 
 <br>
 
    python manage.py createsuperuser
    
# Instalacion de Heroku
Heroku es un servicio de nube en el cual alojaremos nuestra aplicacion web. Para instalarlo primero tendremos 
que instalar el gestor de paquetes.
  <br>
  
    sudo dnf install npm
Una vez teniendo el gestor de paquetes de node, procederemos a instalar heroku con el siguiente comando: 
  <br>
  
    sudo npm install heroku

# Creando una aplicación web desde Django
## Aplicación Blog
Ahora crearemos una aplicación de Blog que permita a los usuarios crear, editar  eliminar publicaciones. 
La pagina de inicio enumerara todas las publicaciones del blog y habrá una pagina de detalle dedicada para cada publicación individual. 

### Configuración inicial: 
Lo primero que haremos será crear un nuevo directorio
[RETBOT@RETBOT ~]$ mkdir blog
[RETBOT@RETBOT ~]$ cd blog
[RETBOT@RETBOT blog]$ pipenv install django
![Instalación-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/instalacionDjango.png)

Para empezar a configurar nuestro proyecto, iniciamos el entorno virtual:

[RETBOT@RETBOT blog]$ pipenv shell <br>
Launching subshell in virtual environment...<br>
 . /home/RETBOT/.local/share/virtualenvs/blog-YSH-3orc/bin/activate<br>

(blog) [RETBOT@RETBOT blog]$ django-admin startproject config .<br>
(blog) [RETBOT@RETBOT blog]$ tree<br>
.<br>
├── config <br>
│   ├── asgi.py <br>
│   ├── __init__.py <br>
│   ├── settings.py <br>
│   ├── urls.py <br>
│   └── wsgi.py <br>
├── manage.py <br>
├── Pipfile <br>
└── Pipfile.lock <br>
 <br>
1 directory, 8 files <br>
   
Creamos una aplicación llamada blog, que sera la entrada inicial de nuestra pagina <br>
(blog) [RETBOT@RETBOT blog]$ python manage.py startapp blog <br>
(blog) [RETBOT@RETBOT blog]$ tree <br>
. <br>
├── blog <br>
│   ├── admin.py <br>
│   ├── apps.py <br>
│   ├── __init__.py <br>
│   ├── migrations <br>
│   │   └── __init__.py <br>
│   ├── models.py <br>
│   ├── tests.py <br>
│   └── views.py <br>
├── config <br>
│   ├── asgi.py <br>
│   ├── __init__.py <br>
│   ├── settings.py <br>
│   ├── urls.py <br>
│   └── wsgi.py <br>
├── manage.py <br>
├── Pipfile <br>
└── Pipfile.lock <br>

Ahora aplicaremos los cambios en nuestra aplicacion <br>
(blog) [RETBOT@RETBOT blog]$  python manage.py migrate <br>
Operations to perform: <br>
  Apply all migrations: admin, auth, contenttypes, sessions <br>
Running migrations: <br>
  Applying contenttypes.0001_initial... OK <br>
  Applying auth.0001_initial... OK <br>
  Applying admin.0001_initial... OK <br>
  Applying admin.0002_logentry_remove_auto_add... OK <br>
  Applying admin.0003_logentry_add_action_flag_choices... OK <br>
  Applying contenttypes.0002_remove_content_type_name... OK <br>
  Applying auth.0002_alter_permission_name_max_length... OK <br>
  Applying auth.0003_alter_user_email_max_length... OK <br>
  Applying auth.0004_alter_user_username_opts... OK <br>
  Applying auth.0005_alter_user_last_login_null... OK <br>
  Applying auth.0006_require_contenttypes_0002... OK <br>
  Applying auth.0007_alter_validators_add_error_messages... OK <br>
  Applying auth.0008_alter_user_username_max_length... OK <br>
  Applying auth.0009_alter_user_last_name_max_length... OK <br>
  Applying auth.0010_alter_group_name_max_length... OK <br>
  Applying auth.0011_update_proxy_permissions... OK <br>
  Applying auth.0012_alter_user_first_name_max_length... OK <br>
  Applying sessions.0001_initial... OK <br>
(blog) [RETBOT@RETBOT blog]$  <br>
   
Para asegurarnos de que Django conozca nuestra nueva aplicación, abra su editor de texto y agregue la nueva aplicación a INSTALLED_APPS en nuestro archivo settings.py ubicado en la carpeta config:

INSTALLED_APPS = [ <br>
    'django.contrib.admin', <br>
    'django.contrib.auth', <br>
    'django.contrib.contenttypes', <br>
    'django.contrib.sessions', <br>
    'django.contrib.messages', <br>
    'django.contrib.staticfiles', <br>
    'blog', <br>
] <br>

(blog) [RETBOT@RETBOT blog]$ python manage.py runserver <br>
Watching for file changes with StatReloader <br>
Performing system checks... <br>

System check identified no issues (0 silenced). <br>
November 13, 2022 - 16:46:17 <br>
Django version 4.1.3, using settings 'config.settings' <br>
Starting development server at http://127.0.0.1:8000/ <br>
Quit the server with CONTROL-C. <br>

Si navega a http://127.0.0.1:8000/ <br>

![Run-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/DjangoRun.png)

Crearemos una nueva aplicación para administrar las publicaciones de nuestro blog  <br>
(blog) [RETBOT@RETBOT blog]python manage.py startapp publicaciones <br>
(blog) [RETBOT@RETBOT blog]$ tree <br>
. <br>
├── blog <br>
│   ├── admin.py <br>
│   ├── apps.py <br>
│   ├── __init__.py <br>
│   ├── migrations <br>
│   │   └── __init__.py <br>
│   ├── models.py <br>
│   ├── tests.py <br>
│   └── views.py <br>
├── config <br>
│   ├── asgi.py <br>
│   ├── __init__.py <br>
│   ├── settings.py <br>
│   ├── urls.py <br>
│   └── wsgi.py <br>
├── db.sqlite3 <br>
├── manage.py <br>
├── Pipfile <br>
├── Pipfile.lock <br>
└── publicaciones <br>
    ├── admin.py <br>
    ├── apps.py <br>
    ├── __init__.py <br>
    ├── migrations <br>
    │   └── __init__.py <br>
    ├── models.py <br>
    ├── tests.py <br>
    └── views.py <br>
 <br>
5 directories, 23 files <br>
(blog) [RETBOT@RETBOT blog]$  <br>


Para asegurarnos de que Django conozca nuestra nueva aplicación, agregue la nueva aplicación a INSTALLED_APPS en nuestro archivo settings.py ubicado en la carpeta config:

INSTALLED_APPS = [ <br>
    'django.contrib.admin', <br>
    'django.contrib.auth', <br>
    'django.contrib.contenttypes', <br>
    'django.contrib.sessions', <br>
    'django.contrib.messages', <br>
    'django.contrib.staticfiles', <br>
    'blog', <br>
    'publicaciones',  # agg <br>
] <br>


Esto significa que la instalación esa completada. A continuación crearemos nuestro modelo de base de datos para publicaciones de blog.<br>
 
## Modelos de base de datos
#### #publicaciones/models.py
from django.db import models <br>
from django.contrib.auth import get_user_model<br>

class Publicacion(models.Model):<br>
  titulo = models.CharField(max_length=200)<br>
  autor = models.ForeignKey(<br>
        get_user_model(),<br>
        on_delete=models.CASCADE,<br>
    )<br>
  cuerpo = models.TextField()<br>
<br>
  def __str__(self):<br>
    return self.titulo<br>
<br>
En la parte superior, estamos importando los modelos de la clase y luego creando una subclase de models.Model llamada Publicación.<br>
Al usar esta funcionalidad de subclase, automáticamente tenemos acceso a todo dentro de django.db.models.Models y podemos agregar campos y métodos adicionales según se desee. <br>
Para el titulo, estamos limitando la longitud a 200 caracteres y para el cuerpo estamos usando un TextField que se expandira automaticamente según sea necesario para adaptarse al texto del usuario. Hay muchos tipos de campos disponibles en Django; puedes ver la lista completa aquí: https://es.acervolima.com/lista-de-campos-y-tipos-de-datos-del-modelo-django/ <br>
   
Para el campo de autor, usamos una ForeignKey que permite una relacion de muchos a uno. Eso significara que un usuario determinado puede ser el autor de muchas publicaciones de blog diferentes, pero no al reves. La referencia es al modelo de usuario integrado que Django proporciona para la autenticacion. Para todas las relaciones de muchos a uno, como ForeignKey, tambien debemos especificar una opcion on_delete. <br>
