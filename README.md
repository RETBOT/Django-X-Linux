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

[RETBOT@RETBOT blog]$ pipenv shell
Launching subshell in virtual environment...
 . /home/RETBOT/.local/share/virtualenvs/blog-YSH-3orc/bin/activate

(blog) [RETBOT@RETBOT blog]$ django-admin startproject config .
(blog) [RETBOT@RETBOT blog]$ tree
.
├── config
│   ├── asgi.py
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── manage.py
├── Pipfile
└── Pipfile.lock

1 directory, 8 files
   
Creamos una aplicación llamada blog, que sera la entrada inicial de nuestra pagina
(blog) [RETBOT@RETBOT blog]$ python manage.py startapp blog
(blog) [RETBOT@RETBOT blog]$ tree
.
├── blog
│   ├── admin.py
│   ├── apps.py
│   ├── __init__.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── tests.py
│   └── views.py
├── config
│   ├── asgi.py
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── manage.py
├── Pipfile
└── Pipfile.lock

Ahora aplicaremos los cambios en nuestra aplicacion
(blog) [RETBOT@RETBOT blog]$  python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying auth.0012_alter_user_first_name_max_length... OK
  Applying sessions.0001_initial... OK
(blog) [RETBOT@RETBOT blog]$ 
   
Para asegurarnos de que Django conozca nuestra nueva aplicación, abra su editor de texto y agregue la nueva aplicación a INSTALLED_APPS en nuestro archivo settings.py ubicado en la carpeta config:

# Application definition
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog',
]



(blog) [RETBOT@RETBOT blog]$ python manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
November 13, 2022 - 16:46:17
Django version 4.1.3, using settings 'config.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.

Si navega a http://127.0.0.1:8000/

![Run-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/DjangoRun.png)
   
