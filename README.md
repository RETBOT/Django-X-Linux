# Curso Practico de Django desde Sistemas Operativos GNU Linux
En este repositorio iremos viendo todo lo necesario para la instalacion de los elementos necesarios 
Pagina web: https://djangoxblog.herokuapp.com/

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

## Configuración inicial: 
Lo primero que haremos será crear un nuevo directorio
[RETBOT@RETBOT ~]$ mkdir blog
   
    mkdir blog
   
[RETBOT@RETBOT ~]$ cd blog
   
    cd blog
   
[RETBOT@RETBOT blog]$ pipenv install django
   
    pipenv install django
   
![Instalación-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/instalacionDjango.png)

Para empezar a configurar nuestro proyecto, iniciamos el entorno virtual:

[RETBOT@RETBOT blog]$ pipenv shell <br>
Launching subshell in virtual environment...<br>
 . /home/RETBOT/.local/share/virtualenvs/blog-YSH-3orc/bin/activate<br>

    pipenv shell  
   
(blog) [RETBOT@RETBOT blog]$ django-admin startproject config .<br>
   
    django-admin startproject config .  
   
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
   
    tree  
   
Creamos una aplicación llamada blog, que sera la entrada inicial de nuestra pagina <br>
(blog) [RETBOT@RETBOT blog]$ python manage.py startapp blog <br>
   
    python manage.py startapp blog    
   
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

    tree    
   
Ahora aplicaremos los cambios en nuestra aplicacion <br>
(blog) [RETBOT@RETBOT blog]$ python manage.py migrate <br>
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
   
    python manage.py migrate  
   
Para asegurarnos de que Django conozca nuestra nueva aplicación, abra su editor de texto y agregue la nueva aplicación a INSTALLED_APPS en nuestro archivo settings.py ubicado en la carpeta config:
```
INSTALLED_APPS = [ 
    'django.contrib.admin', 
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions', 
    'django.contrib.messages', 
    'django.contrib.staticfiles', 
    'blog', 
]
```
(blog) [RETBOT@RETBOT blog]$ python manage.py runserver <br>
Watching for file changes with StatReloader <br>
Performing system checks... <br>

System check identified no issues (0 silenced). <br>
November 13, 2022 - 16:46:17 <br>
Django version 4.1.3, using settings 'config.settings' <br>
Starting development server at http://127.0.0.1:8000/ <br>
Quit the server with CONTROL-C. <br>

Si navega a http://127.0.0.1:8000/ <br>
   
    python manage.py runserver   

![Run-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/DjangoRun.png)

Crearemos una nueva aplicación para administrar las publicaciones de nuestro blog  <br>
(blog) [RETBOT@RETBOT blog]python manage.py startapp publicaciones <br>
   
    python manage.py startapp publicaciones 
   
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

    tree   

Para asegurarnos de que Django conozca nuestra nueva aplicación, agregue la nueva aplicación a INSTALLED_APPS en nuestro archivo settings.py ubicado en la carpeta config:
```
INSTALLED_APPS = [ 
    'django.contrib.admin', 
    'django.contrib.auth', 
    'django.contrib.contenttypes', 
    'django.contrib.sessions', 
    'django.contrib.messages', 
    'django.contrib.staticfiles', 
    'blog', 
    'publicaciones',  # agg 
] 
```

Esto significa que la instalación esa completada. A continuación crearemos nuestro modelo de base de datos para publicaciones de blog.<br>
 
## Modelos de base de datos
```
#publicaciones/models.py
from django.db import models 
from django.contrib.auth import get_user_model

class Publicacion(models.Model):
  titulo = models.CharField(max_length=200)
  autor = models.ForeignKey(
        get_user_model(),
        on_delete=models.CASCADE,
    )
  cuerpo = models.TextField()

  def __str__(self):
    return self.titulo
```
   
En la parte superior, estamos importando los modelos de la clase y luego creando una subclase de models.Model llamada Publicación.<br>
Al usar esta funcionalidad de subclase, automáticamente tenemos acceso a todo dentro de django.db.models.Models y podemos agregar campos y métodos adicionales según se desee. <br>
Para el titulo, estamos limitando la longitud a 200 caracteres y para el cuerpo estamos usando un TextField que se expandira automaticamente según sea necesario para adaptarse al texto del usuario. Hay muchos tipos de campos disponibles en Django; puedes ver la lista completa aquí: https://es.acervolima.com/lista-de-campos-y-tipos-de-datos-del-modelo-django/ <br>
   
Para el campo de autor, usamos una ForeignKey que permite una relacion de muchos a uno. Eso significara que un usuario determinado puede ser el autor de muchas publicaciones de blog diferentes, pero no al reves. La referencia es al modelo de usuario integrado que Django proporciona para la autenticacion. Para todas las relaciones de muchos a uno, como ForeignKey, tambien debemos especificar una opcion on_delete. <br>

Ahora que se creó nuestro nuevo modelo de base de datos, debemos crear un nuevo registro de migración para él y migrar el cambio a nuestra base de datos. Detenga el servidor con Control + c. Este proceso de dos pasos se puede completar con el siguiente comando:<br>

(blog) [RETBOT@RETBOT blog]$ python manage.py makemigrations publicacioneses<br>
Migrations for 'publicaciones':<br>
  publicaciones/migrations/0001_initial.py<br>
    - Create model Publicacion<br>
   
    python manage.py makemigrations publicacioneses 
   
(blog) [RETBOT@RETBOT blog]$ python manage.py migrate<br>
Operations to perform:<br>
  Apply all migrations: admin, auth, contenttypes, publicaciones, sessions<br>
Running migrations:<br>
  Applying publicaciones.0001_initial... OK<br>
(blog) [RETBOT@RETBOT blog]$ <br>
   
    python manage.py migrate

## Admin
Necesitamos una forma de acceder a nuestros datos. ¡Ingrese el administrador de Django! Primero cree una cuenta de superusuario escribiendo el comando a continuación y siguiendo las instrucciones para configurar un correo electrónico y una contraseña. Tenga en cuenta que al escribir su contraseña, no aparecerá en la pantalla por razones de seguridad.<br>
   
(blog) [RETBOT@RETBOT blog]$ python manage.py createsuperuser<br>
Username (leave blank to use 'retbot'): admin<br>
Email address: blogdjango4@gmail.com <br>
Password: <br>
Password (again): <br>
Superuser created successfully.<br>
(blog) [RETBOT@RETBOT blog]$ <br>
   
    python manage.py createsuperuser
   
Ahora comience a ejecutar el servidor Django nuevamente con el comando python manage.py runserver y abra el administrador de Django en http://127.0.0.1:8000/admin/. Inicie sesión con su nueva cuenta de superusuario.<br>
   
![Admin1-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/Admin.png)

Ahora agregaremos las publicaciones al administrador, entraremos a  publicaciones/admin.py <br>
```
from django.contrib import admin
from .models import Publicacion
admin.site.register(Publicacion)
```
   
Si actualiza la página, verá la actualización.<br>
![Admin2-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/Admin2.png)   
Agreguemos dos publicaciones de blog para que tengamos algunos datos de muestra con los que trabajar. Haga clic en el botón + Agregar junto a Publicaciones para crear una nueva entrada. Asegúrate de agregar un "autor" a cada publicación también, ya que por defecto todos los campos del modelo son obligatorios. Si intenta ingresar una publicación sin un autor, verá un error. Si quisiéramos cambiar esto, podríamos agregar opciones de campo a nuestro modelo para hacer que un campo dado sea opcional o llenarlo con un valor predeterminado. <br>
![Pub1-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/Publicacion1.png)
![Pub2-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/Publicacion2.png)   
<br>
Ahora que nuestro modelo de base de datos está completo, necesitamos crear las vistas, URL y plantillas necesarias para que podamos mostrar la información en nuestra aplicación web.<br>
   
   
## URLs
Queremos mostrar las publicaciones de nuestro blog en la página de inicio, así que, como en clases anteriores, primero configuraremos nuestras URLConfs a nivel de proyecto y luego nuestras URLConfs a nivel de aplicación para lograr esto. Tenga en cuenta que "nivel de proyecto" significa en la misma carpeta principal que las carpetas config, blog app y publicaciones app.<br>

Cree un nuevo archivo urls.py dentro de nuestro blog y en las publicaciones:<br>
![Urls1-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/UrlsBlog.png)
![Urls2-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/UrlsPublicaciones.png) 
<br>
   
Ahora agregaremos el siguiente código: <br>
```
# blog/urls.py 
from django.urls import path <br>
from .views import VistaPaginaInicio 
   
urlpatterns = [ 
  path('', VistaPaginaInicio.as_view(), name='inicio'),
] 
```
   
```
 # publicaciones/urls.py 
from django.urls import path
from .views import VistaListaPublicaciones 

urlpatterns = [ 
    path('',VistaListaPublicaciones.as_view(), name='lista_publicaciones'), 
]
```
   
Estamos importando nuestras vistas que se crearán próximamente en la parte superior. La cadena vacía '' le dice a Python que coincida con todos los valores y la convertimos en una URL nombrada, inicio, a la que podemos referirnos en nuestras vistas más adelante. Si bien es opcional agregar una URL con nombre, es una práctica recomendada que debe adoptar, ya que ayuda a mantener las cosas organizadas a medida que aumenta la cantidad de URL.
 <br>
También deberíamos actualizar nuestro archivo urls.py a nivel de proyecto para que sepa reenviar todas las solicitudes directamente a la aplicación del blog.
 <br>
 ```
from django.contrib import admin
from django.urls import path, include 

urlpatterns = [ 
    path('admin/', admin.site.urls),
    path('',include('blog.urls')),
    path('publicaciones/', include('publicaciones.urls')),
]
```
 <br>   
Hemos agregado include en la segunda y tercer línea un patrón de URL con una expresión regular de cadena vacía "" que indica que las solicitudes de URL deben redirigirse tal cual a las URL del blog y a las URL de publicaciones para obtener más instrucciones.   
 <br>   

   
## Vistas
Vamos a utilizar vistas basadas en clases, pero si quieres ver una forma basada en funciones para crear una aplicación de blog, te recomiendo el Tutorial de Django Girls. <br> 
```
# blog/views.py 
from django.views.generic import TemplateView

class VistaPaginaInicio(TemplateView): 
  template_name = 'inicio.html'
 
#publicaciones/views.py
from django.views.generic import ListView 
from .models import Publicacion 

class VistaListaPublicaciones(ListView):
    model = Publicacion
    template_name = 'lista_publicaciones.html' 
```   
En las dos líneas superiores importamos ListView y nuestro modelo de base de datos Publicacion. Luego subclasificamos ListView y agregamos enlaces a nuestro modelo y plantilla. Esto nos ahorra mucho código en comparación con implementarlo todo desde cero. <br> 
   
## Templates
Con nuestras URLConfs y vistas ahora completas, solo nos falta la tercera pieza del rompecabezas: las plantillas. Como ya vimos en clases anteriores, podemos heredar de otras plantillas para mantener nuestro código limpio. Por lo tanto, comenzaremos con un archivo base.html, un archivo inicio.html y un archivo lista_publicaciones.html que heredan de él. Luego, más tarde, cuando agreguemos plantillas para crear y editar publicaciones de blog, también pueden heredar de base.html. <br>
Comience creando nuestro directorio de plantillas a nivel de proyecto con los tres archivos de plantilla. <br>
   
![Django-plantillas](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/plantillas.png)

Luego actualice settings.py para que Django identifique como buscar las plantillas. <br>
```
   TEMPLATES = [
    {
      ... 
        'DIRS': [str(BASE_DIR.joinpath('plantillas'))], 
      ...
            ],
        }, 
    }, 
]  
```   
   
Luego actualice la plantilla base.html de la siguiente manera. <br>
```
<! -- plantillas/base.html -->
<html>
  <head>
    <title>Blog Django</title> 
  </head>
  <body>
      {% block content %} 

      {% endblock content %}
  </body> 
</html>
```
   
Tenga en cuenta que el código entre {% block content%} y {% endblock content%} se puede completar con otras plantillas. Hablando de eso, aquí está el código para inicio.html. <br>

Luego actualice la plantilla base.html de la siguiente manera.
   
```
<!-- plantillas/base.html -->
<html>
  <head>
    <title>Blog Django {% block title%}{% endblock title%}</title>
  </head>
  <body>
      {% block content %}
     
      {% endblock content %}
  </body>
</html>   
```
Tenga en cuenta que el código entre {% block content%} y {% endblock content%} se puede completar con otras plantillas. Hablando de eso, aquí está el código para inicio.html. <br>
   
```
<!-- plantillas/inicio.html -->
{% extends 'base.html' %}

{% block title%}- Inicio{% endblock title%}

{% block content %}
<a href="{% url 'inicio' %}"><h1>Blog en Django</h1></a>
<a href="{% url 'lista_publicaciones' %}">Publicaciones Blog</a>
{% endblock content %}   
```   
   
```   
 <!-- plantillas/lista_publicaciones.html -->
{% extends 'base.html' %}

{% block content %}
  {% for pub in object_list %}
  <div>
    <h2>
      <a href="#"> {{ pub.titulo }}</a>
      <p>{{ pub.cuerpo }}</p>
    </h2>
  </div>
  {% endfor %}
{% endblock content %}  
   
```      
   
En la parte superior notamos que esta plantilla extiende base.html y luego envuelve nuestro código deseado con bloques de contenido. Usamos el lenguaje de plantillas Django para configurar un bucle for simple para cada publicación de blog. Tenga en cuenta que config proviene de ListView y contiene todos los objetos en nuestra vista.<br>
 <br>
Si vuelve a iniciar el servidor Django: python manage.py runserver. Y actualice http://127.0.0.1:8000/, podemos ver que está funcionando.   <br> 
   
![Django-inicio](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/blogInicio.png)
![Django-publicaciones](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/blogPublicaiones.png)   
   
## Imágenes al Blog
Como queremos usar imágenes, necesitamos instalar la librería Pillow, que es necesaria para usar el modelo de datos de Django en imagenes <br>
(blog) [RETBOT@RETBOT blog]$  pip install pillow
   
    pip install pillow

Después debemos entrar en blog/models.py y agregaremos lo siguiente: 
```   
   ...
     imagen = models.ImageField(upload_to="img_pub", null=True)
   ...
```
ImageFiel es un FileFiel con cargas restringidas a formato de imágenes. <br>   
<br> 
Después crearemos una ruta donde cargar las imágenes: <br> 
![Ruta-Imgs](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/rutaImgs.png)
   
   
Dentro del archivo config/settings.py modificaremos lo siguiente:
```   
import os

STATIC_URL = '/static/'
STATICFILES_DIRS = [os.path.join(BASE_DIR, 'static')]

MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
```   
   
y en config/urls.py agregaremos lo siguiente:    
```   
from django.contrib import admin
from django.urls import path, include
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),
    path('',include('blog.urls')),
]

urlpatterns += static(settings.MEDIA_URL, document_root= settings.MEDIA_ROOT)
```      

Ahora entramos en la terminal:  <br> 
(blog) [RETBOT@RETBOT blog]$  python manage.py makemigrations blog <br> 
Migrations for 'blog': <br> 
  blog/migrations/0002_publicacion_img.py <br> 
    - Add field img to publicacion    <br> 
```  
python manage.py makemigrations blog   
```     

(blog) [RETBOT@RETBOT blog]$  python manage.py migrate <br> 
Operations to perform: <br> 
  Apply all migrations: admin, auth, blog, contenttypes, sessions <br> 
Running migrations: <br> 
  Applying blog.0002_publicacion_img... OK <br> 
(blog) [RETBOT@RETBOT blog]$     <br> 
```     
python manage.py migrate   
``` 
   
Iniciamos el servidor para verificar si las imágenes se pueden agregar a las publicaciones.<br>
(blog) [RETBOT@RETBOT blog]$ python manage.py runserver<br>
```     
python manage.py runserver
```    

Entramos en http://127.0.0.1:8000/admin y creamos una nueva publicación <br>
![Img-Publicacion](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/PublicacionImg.png)   
   
