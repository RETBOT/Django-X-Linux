# Curso Practico de Django desde Sistemas Operativos GNU Linux
En este repositorio iremos viendo todo lo necesario para la instalacion de los elementos necesarios <br>
Contacto: <br>
<a href="https://www.facebook.com/profile.php?id=100003493798278">Isaias Gerardo</a><br>
<a href="https://www.facebook.com/robertoesquiveltroncoso">Roberto Esquivel</a> <br>
![img-foro](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/Final%20conferencia%2017%20nov%202022%200911pm.jpeg)

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

# Creando una aplicaci??n web desde Django
## Aplicaci??n Blog
Ahora crearemos una aplicaci??n de Blog que permita a los usuarios crear, editar  eliminar publicaciones. 
La pagina de inicio enumerara todas las publicaciones del blog y habr?? una pagina de detalle dedicada para cada publicaci??n individual. 

## Configuraci??n inicial: 
Lo primero que haremos ser?? crear un nuevo directorio
[RETBOT@RETBOT ~]$ mkdir blog
   
    mkdir blog
   
[RETBOT@RETBOT ~]$ cd blog
   
    cd blog
   
[RETBOT@RETBOT blog]$ pipenv install django
   
    pipenv install django
   
![Instalaci??n-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/instalacionDjango.png)

Para empezar a configurar nuestro proyecto, iniciamos el entorno virtual:

[RETBOT@RETBOT blog]$ pipenv shell <br>
Launching subshell in virtual environment...<br>
 . /home/RETBOT/.local/share/virtualenvs/blog-YSH-3orc/bin/activate<br>

    pipenv shell  
   
(blog) [RETBOT@RETBOT blog]$ django-admin startproject config .<br>
   
    django-admin startproject config .  
   
(blog) [RETBOT@RETBOT blog]$ tree<br>
.<br>
????????? config <br>
??????? ????????? asgi.py <br>
??????? ????????? __init__.py <br>
??????? ????????? settings.py <br>
??????? ????????? urls.py <br>
??????? ????????? wsgi.py <br>
????????? manage.py <br>
????????? Pipfile <br>
????????? Pipfile.lock <br>
 <br>
1 directory, 8 files <br>
   
    tree  
   
Creamos una aplicaci??n llamada blog, que sera la entrada inicial de nuestra pagina <br>
(blog) [RETBOT@RETBOT blog]$ python manage.py startapp blog <br>
   
    python manage.py startapp blog    
   
(blog) [RETBOT@RETBOT blog]$ tree <br>
. <br>
????????? blog <br>
??????? ????????? admin.py <br>
??????? ????????? apps.py <br>
??????? ????????? __init__.py <br>
??????? ????????? migrations <br>
??????? ??????? ????????? __init__.py <br>
??????? ????????? models.py <br>
??????? ????????? tests.py <br>
??????? ????????? views.py <br>
????????? config <br>
??????? ????????? asgi.py <br>
??????? ????????? __init__.py <br>
??????? ????????? settings.py <br>
??????? ????????? urls.py <br>
??????? ????????? wsgi.py <br>
????????? manage.py <br>
????????? Pipfile <br>
????????? Pipfile.lock <br>

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
   
Para asegurarnos de que Django conozca nuestra nueva aplicaci??n, abra su editor de texto y agregue la nueva aplicaci??n a INSTALLED_APPS en nuestro archivo settings.py ubicado en la carpeta config:
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

Crearemos una nueva aplicaci??n para administrar las publicaciones de nuestro blog  <br>
(blog) [RETBOT@RETBOT blog]python manage.py startapp publicaciones <br>
   
    python manage.py startapp publicaciones 
   
(blog) [RETBOT@RETBOT blog]$ tree <br>
. <br>
????????? blog <br>
??????? ????????? admin.py <br>
??????? ????????? apps.py <br>
??????? ????????? __init__.py <br>
??????? ????????? migrations <br>
??????? ??????? ????????? __init__.py <br>
??????? ????????? models.py <br>
??????? ????????? tests.py <br>
??????? ????????? views.py <br>
????????? config <br>
??????? ????????? asgi.py <br>
??????? ????????? __init__.py <br>
??????? ????????? settings.py <br>
??????? ????????? urls.py <br>
??????? ????????? wsgi.py <br>
????????? db.sqlite3 <br>
????????? manage.py <br>
????????? Pipfile <br>
????????? Pipfile.lock <br>
????????? publicaciones <br>
    ????????? admin.py <br>
    ????????? apps.py <br>
    ????????? __init__.py <br>
    ????????? migrations <br>
    ??????? ????????? __init__.py <br>
    ????????? models.py <br>
    ????????? tests.py <br>
    ????????? views.py <br>
 <br>
5 directories, 23 files <br>
(blog) [RETBOT@RETBOT blog]$  <br>

    tree   

Para asegurarnos de que Django conozca nuestra nueva aplicaci??n, agregue la nueva aplicaci??n a INSTALLED_APPS en nuestro archivo settings.py ubicado en la carpeta config:
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

Esto significa que la instalaci??n esa completada. A continuaci??n crearemos nuestro modelo de base de datos para publicaciones de blog.<br>
 
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
   
En la parte superior, estamos importando los modelos de la clase y luego creando una subclase de models.Model llamada Publicaci??n.<br>
Al usar esta funcionalidad de subclase, autom??ticamente tenemos acceso a todo dentro de django.db.models.Models y podemos agregar campos y m??todos adicionales seg??n se desee. <br>
Para el titulo, estamos limitando la longitud a 200 caracteres y para el cuerpo estamos usando un TextField que se expandira automaticamente seg??n sea necesario para adaptarse al texto del usuario. Hay muchos tipos de campos disponibles en Django; puedes ver la lista completa aqu??: https://es.acervolima.com/lista-de-campos-y-tipos-de-datos-del-modelo-django/ <br>
   
Para el campo de autor, usamos una ForeignKey que permite una relacion de muchos a uno. Eso significara que un usuario determinado puede ser el autor de muchas publicaciones de blog diferentes, pero no al reves. La referencia es al modelo de usuario integrado que Django proporciona para la autenticacion. Para todas las relaciones de muchos a uno, como ForeignKey, tambien debemos especificar una opcion on_delete. <br>

Ahora que se cre?? nuestro nuevo modelo de base de datos, debemos crear un nuevo registro de migraci??n para ??l y migrar el cambio a nuestra base de datos. Detenga el servidor con Control + c. Este proceso de dos pasos se puede completar con el siguiente comando:<br>

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
Necesitamos una forma de acceder a nuestros datos. ??Ingrese el administrador de Django! Primero cree una cuenta de superusuario escribiendo el comando a continuaci??n y siguiendo las instrucciones para configurar un correo electr??nico y una contrase??a. Tenga en cuenta que al escribir su contrase??a, no aparecer?? en la pantalla por razones de seguridad.<br>
   
(blog) [RETBOT@RETBOT blog]$ python manage.py createsuperuser<br>
Username (leave blank to use 'retbot'): admin<br>
Email address: blogdjango4@gmail.com <br>
Password: <br>
Password (again): <br>
Superuser created successfully.<br>
(blog) [RETBOT@RETBOT blog]$ <br>
   
    python manage.py createsuperuser
   
Ahora comience a ejecutar el servidor Django nuevamente con el comando python manage.py runserver y abra el administrador de Django en http://127.0.0.1:8000/admin/. Inicie sesi??n con su nueva cuenta de superusuario.<br>
   
![Admin1-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/Admin.png)

Ahora agregaremos las publicaciones al administrador, entraremos a  publicaciones/admin.py <br>
```
from django.contrib import admin
from .models import Publicacion
admin.site.register(Publicacion)
```
   
Si actualiza la p??gina, ver?? la actualizaci??n.<br>
![Admin2-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/Admin2.png)   
Agreguemos dos publicaciones de blog para que tengamos algunos datos de muestra con los que trabajar. Haga clic en el bot??n + Agregar junto a Publicaciones para crear una nueva entrada. Aseg??rate de agregar un "autor" a cada publicaci??n tambi??n, ya que por defecto todos los campos del modelo son obligatorios. Si intenta ingresar una publicaci??n sin un autor, ver?? un error. Si quisi??ramos cambiar esto, podr??amos agregar opciones de campo a nuestro modelo para hacer que un campo dado sea opcional o llenarlo con un valor predeterminado. <br>
![Pub1-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/Publicacion1.png)
![Pub2-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/Publicacion2.png)   
<br>
Ahora que nuestro modelo de base de datos est?? completo, necesitamos crear las??vistas, URL y??plantillas??necesarias para que podamos mostrar la informaci??n en nuestra aplicaci??n web.<br>
   
   
## URLs
Queremos mostrar las publicaciones de nuestro blog en la p??gina de inicio, as?? que, como en clases anteriores, primero configuraremos nuestras URLConfs a nivel de proyecto y luego nuestras URLConfs a nivel de aplicaci??n para lograr esto. Tenga en cuenta que "nivel de proyecto" significa en la misma carpeta principal que las carpetas config, blog app y publicaciones app.<br>

Cree un nuevo archivo urls.py dentro de nuestro blog y en las publicaciones:<br>
![Urls1-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/UrlsBlog.png)
![Urls2-Django](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/UrlsPublicaciones.png) 
<br>
   
Ahora agregaremos el siguiente c??digo: <br>
```
# blog/urls.py 
from django.urls import path
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
   
Estamos importando nuestras vistas que se crear??n pr??ximamente en la parte superior. La cadena vac??a '' le dice a Python que coincida con todos los valores y la convertimos en una URL nombrada, inicio, a la que podemos referirnos en nuestras vistas m??s adelante. Si bien es opcional agregar una URL con nombre, es una pr??ctica recomendada que debe adoptar, ya que ayuda a mantener las cosas organizadas a medida que aumenta la cantidad de URL.
 <br>
Tambi??n deber??amos actualizar nuestro archivo urls.py a nivel de proyecto para que sepa reenviar todas las solicitudes directamente a la aplicaci??n del blog.
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
Hemos agregado include en la segunda y tercer l??nea un patr??n de URL con una expresi??n regular de cadena vac??a "" que indica que las solicitudes de URL deben redirigirse tal cual a las URL del blog y a las URL de publicaciones para obtener m??s instrucciones.   
 <br>   

   
## Vistas
Vamos a utilizar vistas basadas en clases, pero si quieres ver una forma basada en funciones para crear una aplicaci??n de blog, te recomiendo el Tutorial de Django Girls. <br> 
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
En las dos l??neas superiores importamos ListView y nuestro modelo de base de datos Publicacion. Luego subclasificamos ListView y agregamos enlaces a nuestro modelo y plantilla. Esto nos ahorra mucho c??digo en comparaci??n con implementarlo todo desde cero. <br> 
   
## Templates
Con nuestras URLConfs y vistas ahora completas, solo nos falta la tercera pieza del rompecabezas: las plantillas. Por lo tanto, comenzaremos con un archivo base.html, un archivo inicio.html y un archivo lista_publicaciones.html que heredan de ??l. Luego, m??s tarde, cuando agreguemos plantillas para crear y editar publicaciones de blog, tambi??n pueden heredar de base.html. <br>
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
   

   <br>
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
Tenga en cuenta que el c??digo entre {% block content%} y {% endblock content%} se puede completar con otras plantillas. Hablando de eso, aqu?? est?? el c??digo para inicio.html. <br>
   
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
   
En la parte superior notamos que esta plantilla extiende base.html y luego envuelve nuestro c??digo deseado con bloques de contenido. Usamos el lenguaje de plantillas Django para configurar un bucle for simple para cada publicaci??n de blog. Tenga en cuenta que config proviene de ListView y contiene todos los objetos en nuestra vista.<br>
 <br>
Si vuelve a iniciar el servidor Django: python manage.py runserver. Y actualice http://127.0.0.1:8000/, podemos ver que est?? funcionando.   <br> 
   
![Django-inicio](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/blogInicio.png)
![Django-publicaciones](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/blogPublicaiones.png)   
   
## Im??genes al Blog
Como queremos usar im??genes, necesitamos instalar la librer??a Pillow, que es necesaria para usar el modelo de datos de Django en imagenes <br>
(blog) [RETBOT@RETBOT blog]$  pip install pillow
   
    pip install pillow

Despu??s debemos entrar en blog/models.py y agregaremos lo siguiente: 
```   
   ...
     imagen = models.ImageField(upload_to="img_pub", null=True)
   ...
```
ImageFiel es un FileFiel con cargas restringidas a formato de im??genes. <br>   
<br> 
Despu??s crearemos una ruta donde cargar las im??genes: <br> 
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
(blog) [RETBOT@RETBOT blog]$  python manage.py makemigrations publicacion <br> 
Migrations for 'blog': <br> 
  blog/migrations/0002_publicacion_img.py <br> 
    - Add field img to publicacion    <br> 
```  
python manage.py makemigrations publicaciones   
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
   
Iniciamos el servidor para verificar si las im??genes se pueden agregar a las publicaciones.<br>
(blog) [RETBOT@RETBOT blog]$ python manage.py runserver<br>
```     
python manage.py runserver
```    

Entramos en http://127.0.0.1:8000/admin y creamos una nueva publicaci??n <br>
![Img-Publicacion](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/PublicacionImg.png)   
   
## Bootstrap
Entramos al archivo base.html ubicado en las plantillas <br>
``` 
<head>
  <meta charset="UTF-8">
  <title>Blog Django {% block title %}{% endblock title %}</title>
  <meta name="viewport" content="with=device.width, initial-scale=1, 
      shrink-to-fit=no">
  <!-- CSS BootStrap -->
  <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" crossorigin="anonymous"
    rel="stylesheet">
</head>
```    
   
y al final del archivo
```  
<!-- JavaScript Opcional -->
    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js/1.14.3/umd/popper.min.js" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js"
      crossorigin="anonymous"></script>
  </body>
</html>
```     
    
### Ahora personalizaremos nuestro blog    
#### base.html    
```        
<!-- plantillas/base.html -->
<html>
<head>
  <meta charset="UTF-8">
  <title>Blog Django {% block title %}{% endblock title %}</title>
  <meta name="viewport" content="with=device.width, initial-scale=1, 
      shrink-to-fit=no">
  <!-- CSS BootStrap -->
  <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" crossorigin="anonymous"
    rel="stylesheet">
</head>

<body>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <a class="navbar-brand" href="{% url 'inicio' %}">
      Blog Django
    </a>
    <div class="navbar-collapse" id="navbarSupportedContent">
      {% if user.is_authenticated %}
      <ul class="navbar-nav ml-auto">
        <li class="nav-item">
          <a class="nav-link dropdown-toggle" href="#" role="button" id="navbarDropdown" data-toggle="dropdown"
            aria-haspopup="true" aria-expanded="false">
            Blogs
          </a>
          <div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbarDropdown">
            <a class="dropdown-item" href="#">
              Blogs
            </a>
            <a class="dropdown-item" href="#">
              Nuevo
            </a>
          </div>
        </li>
        <li class="nav-item">
          <a class="nav-link dropdown-toggle" href="#" role="button" id="navbarDropdown" data-toggle="dropdown"
            aria-haspopup="true" aria-expanded="false">
            {{ user.username }}
          </a>
          <div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbarDropdown">
            <a class="dropdown-item" href="#">
              Cambiar Contrase??a
            </a>
            <a class="dropdown-item" href="#">
              Salir
            </a>
          </div>
        </li>
      </ul>
      {% else %}
      <form class="form-inline ml-auto">
        <a href="#" class="btn btn-outline-secondary">
          Acceder
        </a>
        <a href="#" class="btn btn-primary ml-2">
          Registrarse
        </a>
      </form>
      {% endif %}
    </div>
  </nav>
    {% block content %}
    
    {% endblock content %}
  <!-- JavaScript Opcional -->
  <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" crossorigin="anonymous"></script>
  <script src="https://cdn.jsdelivr.net/npm/popper.js/1.14.3/umd/popper.min.js" crossorigin="anonymous"></script>
  <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js" crossorigin="anonymous"></script>
</body>
</html>  
```        
#### inicio.html    
```  
<!-- plantillas/inicio.html -->
{% extends 'base.html' %}

{% block title%}- Inicio{% endblock title%}

{% block content %}
<main role="main" class="container">
  <h1 class="display-4">Blog Django</h1>
  <div class="jumbotron">
    <p class="lead">Un blog hecho con Django.</p>
    <p class="lead">
      <a class="btn btn-lg btn-primary" 
      href="{% url 'lista_publicaciones' %}" 
      role="button">Entrar</a>
    </p>
  </div>
</main>
{% endblock content %}    
```      
#### lista_publicaciones.html 
```  
<!-- plantillas/lista_publicaciones.html -->
{% extends 'base.html' %}

{% block title %} - Publicaciones {% endblock title %}

{% block content %}
<br>
<div class="jumbotron p-md-2 text-white rounded bg-dark">
  <h1 class="display-4 font-italic text-center" >Publicaciones</h1>
</div>

  {% for pub in object_list %}

  <div class="col-md-12">
    <div class="card flex-md-row mb-3 box-shadow h-md-270">
      <div class="card-body d-flex flex-column align-items-center">
        <strong class="d-inline-block mb-2 text-primary">Autor: {{ pub.autor }}</strong>
        <h3 class="mb-0">
          <a class="text-dark" href="#">{{ pub.titulo }} </a>
        </h3>
        <p class="card-text mb-auto">{{ pub.cuerpo }} </a>
      </div>
    </div>
  </div>
  {% endfor %}
{% endblock content %}    
```      

Teniendo nuestra pagina personalizada ahora queda darle mas funcionalidades, por lo cual agregaremos la forma en la que podremos crear una nueva publicaci??n, ver detalladamente, editar la publicaci??n y eliminarla:<br>
    
Crearemos los url para poder acceder a las paginas, desde publicaciones/urls.py  <br>
#### publicaciones/urls.py   
```     
# publicaciones/urls.py
from django.urls import path
from .views import (
    VistaListaPublicaciones,
    VistaCrearPublicacion,
    VistaEditarPublicacion,
    VistaDetallePublicacion,
    VistaEliminarPublicacion,
    )

urlpatterns = [
    path('',VistaListaPublicaciones.as_view(), name='lista_publicaciones'),
    path('nuevo/',VistaCrearPublicacion.as_view(), name='nueva_publicacion'),
    path('<int:pk>/editar/',VistaEditarPublicacion.as_view(), name='editar_publicacion'),
    path('<int:pk>/detalle/',VistaDetallePublicacion.as_view(), name='detalle_publicacion'),
    path('<int:pk>/eliminar/',VistaEliminarPublicacion.as_view(), name='eliminar_publicacion'),
]    
```     
####  publicaciones/views.py   
```       
#publicaciones/views.py
from django.views.generic import ListView, DetailView
from django.views.generic.edit import DeleteView, UpdateView, CreateView
from django.urls import reverse_lazy
from .models import Publicaciones

# Create your views here.
class VistaListaPublicaciones(ListView):
  model = Publicaciones
  template_name = 'lista_publicaciones.html'

class VistaCrearPublicacion(CreateView):
  model = Publicaciones
  template_name = 'nueva_publicacion.html'
  fields = ['titulo', 'cuerpo', 'imagen',]

class VistaDetallePublicacion(DetailView):
  model = Publicaciones
  template_name = 'detalle_publicacion.html'
  context_object_name = 'pub'
  
class VistaEditarPublicacion(UpdateView):
  model = Publicaciones
  template_name = 'editar_publicacion.html'
  fields = ['titulo', 'cuerpo', 'imagen',]
  context_object_name = 'pub'

class VistaEliminarPublicacion(DeleteView):
  model = Publicaciones
  template_name = 'eliminar_publicacion.html'
  context_object_name = 'pub'
  success_url = reverse_lazy('lista_publicaciones') 
```       
    
Crearemos 4 nuevos archivos para crear una nueva publicaci??n, ver detalladamente, editar la publicaci??n y eliminarla <br>
nueva_publicacion.html <br>
detalle_publicacion.html <br>
editar_publicacion.html <br>
eliminar_publicacion.html <br>
![Django-Templates](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/CRUD.png)   
 
#### Iniciamos modificando nueva_publicacion.html    
```  
<!--planillas/nueva_publicacion.html -->
{% extends 'base.html' %}
{% block title %} - Nueva Publicacion {% endblock title %}

{% block content %}
<div class="form-group">
  <h1>Nueva Publicacion</h1>
  <form enctype="multipart/form-data" action="" method="post">{% csrf_token %}
      {{ form.as_p }}
      <input class="btn btn-success" type="submit" value="Guardar cambios" style="color: black;">
  </form>
</div>
{% endblock content %}
```  
Cargamos la direccion http://127.0.0.1:8000/publicaciones/nueva/ para validar que nuestra pagina esta funcionado   <br>  
![Django-Nueva-Publicacion](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/NuevaPublicacion.png)       

y redireccionamos al usuario a la pagina de detalle  <br>      
```    
# publicaciones/models.py
...
from django.urls import reverse

# Create your models here.
class Publicacion(models.Model):
  titulo = models.CharField(max_length=200)
  cuerpo = models.TextField()
  imagen = models.ImageField(upload_to="img_pub", null=True)
  autor = models.ForeignKey(
        get_user_model(),
        on_delete=models.CASCADE,
    )

  def __str__(self):
    return self.titulo

  def get_absolute_url(self):
        return reverse('detalle_publicacion',args=[str(self.id)])
```  
    
#### Ahora modificaremos detalle publicaciones
```
<!-- plantillas/detalle_publicacion.html -->
{% extends 'base.html' %}

{% block title %} - Detalle Publicacion{% endblock title %}

{% block content %}
<br>

        <div class="card">
            <div class="card-header">
              <div class="jumbotron p-md-2 text-white rounded bg-dark">
                <h1 class="display-4 font-italic text-center" >{{ pub.titulo }}</h1>
              </div>
                <span class="text-muted">Creado por {{ pub.autor }}</span>
            </div>
            <div class="card-body">
                {{ pub.cuerpo }}
            </div>
            {% if pub.imagen.url != null %}
            <center>
              <img class="img-fluid" src="{{ pub.imagen.url }}" alt="Imagen blog">
            </center>
            {% endif %}
            </div>
            
            <div class="card-footer text-center text-muted">
                <a href="#">Editar</a> | 
                <a href="#">Eliminar</a> |
                <a href="#">Volver a Publicaciones</a>
            </div>
        </div>
{% endblock content %}
``` 
    
y configuramos la ruta en lista publicaci??n, en plantillas/lista_publicaciones.html
``` 
<a class="text-dark" href="{% url 'detalle_publicacion' pub.pk %}">{{ pub.titulo }} </a>
```  
Tambi??n configuramos la pagina principal en plantillas/base.html   
```   
<a class="dropdown-item" href="{% url 'lista_publicaciones' %}">
   Blogs
</a>
<a class="dropdown-item" href="{% url 'nueva_publicacion' %}">
   Nuevo
</a>  
```  
    
#### Ahora configuraremos editar_publicaciones.html de plantillas    
```
<!-- plantillas/editar_publicacion.html -->
{% extends 'base.html' %}

{% block title %} - Editar Publicaci??n{% endblock title %}

{% block content %}
<h1>Editar publicacion</h1>
<form enctype="multipart/form-data" action="" method="post">{% csrf_token %}
    {{ form.as_p }}
    <input class="btn btn-success ml-2" type="submit" value="Guardar cambios" style="color: black;">
</form>
{% endblock content %} 
```
    
#### y eliminar_publicaciones.html de plantillas  
```
<!-- plantillas/eliminar_publicaciones.html -->
{% extends 'base.html' %}

{% block title %} - Eliminar Publicaci??n{% endblock title %}

{% block content %}
    <h1>Eliminar publicacion</h1>
    <form action="" method="post">{% csrf_token %}
        <p>??Est?? completamente seguro de que desea eliminar "{{ object.titulo }}" ? </p>
        <input class="btn btn-danger ml-2" type="submit" value="Confirmar eliminarci??n" style="color: black;">        
    </form>
{% endblock content %} 
```
    
#### en detalle_publicacion.html de plantillas agregaremos las urls
``` 
<div class="card-footer text-center text-muted">
     <a href="{% url 'editar_publicacion' pub.pk %}">Editar</a> | 
     <a href="{% url 'eliminar_publicacion' pub.pk %}">Eliminar</a> |
     <a href="{% url 'lista_publicaciones' %}">Volver a Publicaciones</a>
</div>
```
    
## Administrar cuentas de usuarios
Iniciaremos creando una aplicaci??n llamada cuentas
(blog) [RETBOT@RETBOT blog]$ python manage.py startapp cuentas
``` 
python manage.py startapp cuentas
``` 
(blog) [RETBOT@RETBOT blog]$ tree  
```   
tree  
``` 
. <br>
????????? blog <br>
??????? ????????? admin.py <br>
??????? ????????? apps.py <br>
??????? ????????? __init__.py <br>
??????? ????????? migrations <br>
??????? ??????? ????????? __init__.py <br>
??????? ????????? models.py <br>
??????? ????????? tests.py <br>
??????? ????????? urls.py <br>
??????? ????????? views.py <br>
????????? config <br>
??????? ????????? asgi.py <br>
??????? ????????? __init__.py <br>
??????? ????????? settings.py <br>
??????? ????????? urls.py <br>
??????? ????????? wsgi.py <br>
????????? cuentas <br>
??????? ????????? admin.py <br>
??????? ????????? apps.py <br>
??????? ????????? __init__.py <br>
??????? ????????? migrations <br>
??????? ??????? ????????? __init__.py <br>
??????? ????????? models.py <br>
??????? ????????? tests.py <br>
??????? ????????? views.py <br>
????????? db.sqlite3 <br>
????????? manage.py <br>
????????? media <br>
??????? ????????? img_pub <br>
???????     ????????? logo2.png <br>
???????     ????????? logo.jpg <br>
????????? Pipfile <br>
????????? Pipfile.lock <br>
????????? plantillas <br>
??????? ????????? base.html <br>
??????? ????????? detalle_publicacion.html <br>
??????? ????????? editar_publicacion.html <br>
??????? ????????? eliminar_publicacion.html <br>
??????? ????????? inicio.html <br>
??????? ????????? lista_publicaciones.html <br>
??????? ????????? nueva_publicacion.html <br>
????????? publicaciones <br>
??????? ????????? admin.py <br>
??????? ????????? apps.py <br>
??????? ????????? __init__.py <br>
??????? ????????? migrations <br>
??????? ??????? ????????? 0001_initial.py <br>
??????? ??????? ????????? __init__.py <br>
??????? ????????? models.py <br>
??????? ????????? tests.py <br>
??????? ????????? urls.py <br>
??????? ????????? views.py <br>
????????? static <br>
 <br>
11 directories, 45 files  <br>
<br>    
Agregamos la nueva aplicaci??n a config/settings.py de config para que pueda ser reconocido 
```  
# Application definition
INSTALLED_APPS = [
...

     # locales
    'blog',
    'publicaciones',
    'cuentas', 
]
```
y tambi??n la configuracion de cuentas de usuario personalizada debro de config/settings.py
```
AUTH_USER_MODEL = 'cuentas.UsuarioPers'
``` 
despues entramos a urls.py de config:  
```
urlpatterns = [
    path('admin/', admin.site.urls),
    path('cuentas/', include('django.contrib.auth.urls')), #
    path('cuentas/', include('cuentas.urls')), #
    path('',include('blog.urls')),
    path('publicaciones/', include('publicaciones.urls')),
]
``` 
Para la configuraci??n de las urls de las cuentas, primero crearemos un archivo llamado urls.py dentro de la aplicaci??n cuentas: <br>
![Django-Cuentas-URLs](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/UrlsCuentas.png) <br>
Dentro de urls.py
``` 
# cuentas/urls.py
from urllib.parse import urlparse
from django.urls import path
from .views import VistaRegistro

urlpatterns = [
    path('registro/', VistaRegistro.as_view(), name='signup'),
]
``` 
y configuramos las views.py de cuentas, para tener la vista de usuarios 
```    
from audioop import reverse
from django.urls import reverse_lazy
from django.views.generic import CreateView
from .forms import FormularioCreacionUsuarioPers

# Create your views here.
class VistaRegistro(CreateView):
    form_class = FormularioCreacionUsuarioPers
    success_url = reverse_lazy('login')
    template_name = 'registration/signup.html'
``` 
    
Despu??s creamos un archivo llamado forms.py dentro de cuentas: <br>
![Django-FormsCuentas](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/formsCuentas.png)
```
#cuentas/froms.py
from django import forms
from django.contrib.auth.forms import UserCreationForm, UserChangeForm
from .models import UsuarioPers

class FormularioCreacionUsuarioPers(UserCreationForm):
    class Meta(UserCreationForm):
        model = UsuarioPers
        fields = ('username','email','edad',)

class FormularioCambioUsuarioPers(UserChangeForm):
    class Meta:
        model = UsuarioPers
        fields = ('username','email','edad',)
```
    
Y despu??s lo agregaremos a admin.py para que pueda ser desplegado en la pagina del administrador 
```   
#cuentas/admin.py
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin
from .forms import FormularioCambioUsuarioPers, FormularioCreacionUsuarioPers
from .models import UsuarioPers

# Register your models here.
class UsuarioPersAdmin(UserAdmin):
    add_form = FormularioCreacionUsuarioPers
    form = FormularioCambioUsuarioPers
    model = UsuarioPers
    list_display = ['email', 'username', 'edad', 'is_staff',]
    fieldsets = UserAdmin.fieldsets + (
        (None, {'fields': ('edad',)}),
    )
    add_fieldsets = UserAdmin.add_fieldsets + (
        (None, {'fields': ('edad',)}),
    )

admin.site.register(UsuarioPers, UsuarioPersAdmin)
``` 
Lo que falta es migrar la informaci??n a la base de datos, pero tenemos que tener en cuenta, que estamos utilizando un modelo de usuarios personalizados, primero tenemos que comentar 
``` 
INSTALLED_APPS = [
    #'django.contrib.admin',
???
]
``` 
y tambi??n en urls.py de config   
```  
urlpatterns = [
    #path('admin/', admin.site.urls),
  ...
] 
``` 
Despu??s eliminaremos las migraciones de publicaciones ya que estamos utilizando los modelos de usuarios y causa conflicto en la migraci??n de usuario <br>
![Django-Elim-Migracion](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/ElimMigracion.png)  <br>
Iniciamos las migraciones de la aplicaci??n cuentas <br>
    
(blog) [RETBOT@RETBOT blog]$ python manage.py makemigrations cuentas <br>
Migrations for 'cuentas': <br>
  cuentas/migrations/0001_initial.py <br>
    - Create model UsuarioPers <br>
    
```   
python manage.py makemigrations cuentas
``` 
    
(blog) [RETBOT@RETBOT blog]$ python manage.py migrate <br>
Operations to perform: <br>
  Apply all migrations: auth, contenttypes, cuentas, sessions <br>
Running migrations: <br>
  Applying cuentas.0001_initial... OK <br>
```  
python manage.py migrate 
```   
y despu??s des-comentamos el c??digo comentado anteriormente y hacemos la migraci??n en publicaciones   <br> 
(blog) [RETBOT@RETBOT blog]$ python manage.py makemigrations publicaciones <br>
Migrations for 'publicaciones': <br>
  publicaciones/migrations/0001_initial.py <br>
    - Create model Publicacion     <br>
    
```   
python manage.py makemigrations publicaciones
``` 
    
(blog) [RETBOT@RETBOT blog]$ python manage.py migrate <br>
Operations to perform: <br>
  Apply all migrations: admin, auth, contenttypes, cuentas, publicaciones, sessions <br>
Running migrations: <br>
  No migrations to apply. <br>
(blog) [RETBOT@RETBOT blog]$  <br>  

```  
python manage.py migrate
``` 
    
Como cambiamos autenticaci??n de usuario tenemos que crear nuevamente un usuario de administraci??n <br> 
(blog) [RETBOT@RETBOT blog]$ python manage.py createsuperuser <br> 
Username: admin <br> 
Email: robertoesquiveltr16@gmail.com <br> 
Password:  <br> 
Password (again):  <br> 
Superuser created successfully. <br> 
(blog) [RETBOT@RETBOT blog]$  <br> 
    
```   
python manage.py createsuperuser
```   
    
## Login  
Creamos una carpeta en plantillas llamada registration y dentro de la carpeta creamos un nuevo archivo llamado login.html <br>
![plantillas_login](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/plantillas_login.png)   
``` 
<!-- plantillas/registration/login.html -->
{% extends 'base.html' %}
{% block title %}- Acceso{% endblock title %}

{% block content %}
<h1>Bienvenido</h1>
    <h2>Iniciar Sesi??n</h2><br>
    <form method="post">{% csrf_token %}
        {{ form.as_p }}
        <input class="btn btn-success ml-2" type="submit" value="Acceder (Iniciar Sesi??n)" style="color: black;">
    </form>
    <br>
    <a href="{% url 'password_reset' %}" type="button" class="formulario__submit" style="color: black;">??Olvido su contrase??a?</a>
{% endblock content %}
```   
En la misma carpeta creamos un archivo llamado signup.html, el cual tendr?? el siguiente c??digo:  
``` 
<!-- plantillas/registration/signup.html -->
{% extends 'base.html' %}
{% block title %}-Registro{% endblock title %} 

{% block content %}
<br><h2>Registro</h2><br>
<form method="post"> {% csrf_token %} 
    {{ form.as_p }}
    <input class="btn btn-success ml-2" type="submit" value="Registro" style="color: black;">
</form>
{% endblock content %} 
``` 
Agregamos la url para cambiar contrase??a, salir, acceder e iniciar sesi??n a base.html
``` 
<a class="dropdown-item" href="{% url 'password_change' %}">
     Cambiar Contrase??a
</a>
<a class="dropdown-item" href="{% url 'logout' %}">
     Salir
</a>
``` 
```    
<a href="{% url 'login' %}" class="btn btn-outline-secondary">
  Acceder
</a>
<a href="{% url 'signup' %}" class="btn btn-primary ml-2">
  Registrarse
</a>
```  
Ahora crearemos un archivo llamado password_change_done y password_change_form para cambiar la contrase??a
```  
<!-- plantillas/registration/password_change_form.htnl -->
{% extends 'base.html' %}

{% block title %}- Cambio de contrasela{% endblock title %}

{% block content %}

    <h2>Cambio de contrase??a</h2>
    <p>Por favor introduzca su contrasela anterior.  por razones de seguridad,
        y luego introduzca su nueva contrase??a dos veces para poder verificar que la escribi?? 
        correctamente.</p>
        <div class="registro">
            <div class="registro_contenido">
        <form  method="post">{% csrf_token %}{{ form.as_p }}
            <input class="btn btn-success ml-2" type="submit" value="Cambiar contrase??a" style="color: black;">
        </form>
    </div>
</div>
{% endblock content %}
```   
    
```  
<!-- plantillas/registration/password_change_done.html -->
{% extends 'base.html' %}

{% block title %}- Contrase??a modificada satisfactoriamente {% endblock title %}  

{% block content %}
    <h1>Contrase??a modificada satisfactoriamente</h1>
    <p style="text-align: center;">Su contrase??a fue modificada</p>
{% endblock content %}
```   
Ahora para restaurar la contrase??a debemos configurar el envi?? de correos electr??nicos en django
para eso necesitamos entrar a la carpeta config y en el archivo settings.py agregar los siguiente: <br>
La primera linea sirve para hacer pruebas desde la consola  
```  
EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'
```  
Lo segundo sirve para configurar el envio de correos electronicos desde nuestra cuenta de google
```   
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_PORT = '587'
EMAIL_HOST_USER = 'blogdjango4@gmail.com'
EMAIL_HOST_PASSWORD = 'contrase??a'
EMAIL_USE_TLS = True
DEFAULT_FROM_EMAIL = 'blogdjango4@gmail.com' 
```  
Para agregar la contrase??a debemos entrar al perfil y en administrar tu cuenta>Seguridad <br>
![AdmCuenta](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/adminCuenta.png)  <br>
![Seguridad](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/seguridad.png) <br>

Debemos tener activada la verificaci??n en 2 pasos <br>
![ver2pasos](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/verif2pasos.png) <br>
y seleccionaremos la contrase??a de aplicaciones <br>
![contrasenha](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/GeneraContrase%C3%B1a.png)<br>
Seleccionamos generar y se mostrara la contrase??a que ingresaremos EMAIL_HOST_PASSWORD en config/settings.py <br>

Ya teniendo la configuraci??n, crearemos los siguientes archivos <br>
password_change_done.html <br>
password_change_form.html <br>
password_reset_complete.html <br>
password_reset_confirm.html <br>
password_reset_done.html <br>
password_reset_form.html <br>
![plantillas](https://github.com/RETBOT/Django-X-Linux/blob/main/imgs/PlantillasFull.png)
    
Los cuales tendran los siguientes codigos:  
```  
<!-- plantillas/registration/password_change_done.html -->
{% extends 'base.html' %}

{% block title %}- Contrase??a modificada satisfactoriamente {% endblock title %}  

{% block content %}
    <h1>Contrase??a modificada satisfactoriamente</h1>
    <p style="text-align: center;">Su contrase??a fue modificada</p>
{% endblock content %}  
```  
    
```  
<!-- plantillas/registration/password_change_form.htnl -->
{% extends 'base.html' %}

{% block title %}- Cambio de contrasela{% endblock title %}

{% block content %}

    <h2>Cambio de contrase??a</h2>
    <p>Por favor introduzca su contrasela anterior.  por razones de seguridad,
        y luego introduzca su nueva contrase??a dos veces para poder verificar que la escribi?? 
        correctamente.</p>
        <div class="registro">
            <div class="registro_contenido">
        <form  method="post">{% csrf_token %}{{ form.as_p }}
            <input class="btn btn-success ml-2" type="submit" value="Cambiar contrase??a" style="color: black;">
        </form>
    </div>
</div>
{% endblock content %}
``` 
    
``` 
<!-- plantillas/registration/password_reset_complete.htnl -->
{% extends 'base.html' %}

{% block title %}- Restablecimiento de contrase??a completo {% endblock title %} 

{% block content %}
    <h1>Restablecimiento de contrase??a completo</h1>
    <p>Su nueva contrasela ha sido reestablecida. <br>Puede iniciar sesi??n ahora en  la 
    <a href="{% url 'login' %}">P??gina de acceso</a>
    </p>
{% endblock content %}
```
    
```  
<!-- plantillas/registration/password_reset_confirm.htnl -->
{% extends 'base.html' %}

{% block title %}- Introduzca su nueva contrase??a {% endblock title %} 

{% block content %}
    <h1>Establezca su nueva contrase??a</h1>
    <div class="registro">
        <div class="registro_contenido">
    <form method="post"> {% csrf_token %}
        {{ form.as_p }}
        <input class="btn btn-success ml-2" type="submit" value="Cambiar mi contrase??a" style="color: black;">
    </form>
</div>
</div>
{% endblock content %}
```
    
``` 
<!-- plantillas/registration/password_reset_done.htnl -->
{% extends 'base.html' %}

{% block title %}- Email enviado {% endblock title %}

{% block content %}
    <h1>Verifique su buz??n de entrada</h1>
    <p>Le hemos enviado instrucci??nes para restablecer su contrase??a, por una nueva.
        Deberoa de recibir el correo en unos minutos! </p>
{% endblock content %}
```
    
```  
<!-- plantillas/registration/password_reset_form.htnl -->
{% extends 'base.html' %}

{% block content %}
    <h1>??Olvido su contrase??a?</h1>
    <p>Introdusca su email abajo, y le enviaremos instrucciones para establecer una nueva contrase??a </p>
    <div class="registro">
        <div class="registro_contenido">
    <form method="post"> {% csrf_token %}
        {{ form.as_p }}
        <input class="btn btn-success ml-2" type="submit" value="Enviarme instrucciones" style="color: black;">
    </form>
    </div>
</div>
{% endblock content %}
    
```
    
    
## Configuraci??n de privacidad  
Entramos a views.py de publicaciones e importamos lo siguiente 
``` 
    from django.contrib.auth.mixins import (
    LoginRequiredMixin,
    UserPassesTestMixin
    )
```
Agregamos  LoginRequiredMixin a la vista crear publicacion:  
```   
class VistaCrearPublicacion(LoginRequiredMixin, CreateView):
    model = Publicacion
    template_name = 'nueva_publicacion.html'
    fields = ['titulo', 'cuerpo','imagen']

    login_url = 'login'
    
    def form_valid(self, form):
        form.instance.autor = self.request.user
        return super().form_valid(form)
```  
y LoginRequiredMixin, UserPassesTestMixin a editar y eliminar
```  
class VistaEditarPublicacion(LoginRequiredMixin, UserPassesTestMixin, UpdateView):
    model = Publicacion
    template_name = 'editar_publicacion.html'
    fields = ['titulo', 'cuerpo','imagen',]
    login_url = 'login'

    def test_func(self):
        obj = self.get_object()
        return obj.autor == self.request.user

class VistaEliminarPublicacion(LoginRequiredMixin, UserPassesTestMixin, DeleteView):
    model = Publicacion
    template_name = 'eliminar_publicacion.html'
    success_url = reverse_lazy('lista_publicaciones')
    login_url = 'login'

    def test_func(self):
        obj = self.get_object()
        return obj.autor == self.request.user
```   
y en settings.py de config agregamos, para redireccionar al usuario a la p??gina de inicio:  
```  
LOGIN_REDIRECT_URL = 'inicio'
LOGOUT_REDIRECT_URL = 'inicio'  
```  

Esto para que solo el creador de la publicaci??n pueda eliminar la publicaci??n   

## INSTALACION Y CONFIGURACION DE HEROKU
Heroku por as?? decirlo es como una nube, en la cual podremos subir nuestra aplicaci??n web. <br>
Existen diversas formas de instalar heroku en gnu/Linux, mas sin embargo utilizaremos una forma global de instalar en cualquier distribuci??n Linux.  <br>
Para ello se hara con el siguiente comando :
curl https://cli-assets.heroku.com/install.sh | sh
```
curl https://cli-assets.heroku.com/install.sh | sh
```
Una vez hecho esto, podremos continuar con los siguientes pasos.    

## CONFIGURACION DE HEROKU 
Ejecutar pipenv lock para generar el Pipfile.lock apropiado <br>
```  
pipenv lock
```
Luego creamos un Procfile que le diga a Heroku como ejecutar el servidor remoto vivir?? nuestro c??digo.
```
touch Procfile
```    
Por ahora, le estamos diciendo a Heroku en el archivo Procfile que use gunicorn como nuestro servidor de producci??n y busque en nuestro archivo config.wsgi para obtener mas instrucciones.
```   
web: gunicorn config.wsgi ???log-file ??? 
```   
A continuaci??n, instale gunicorn que usaremos en producci??n mientras seguimos usando el servidor interno de Django para uso de desarrollo local.
``` 
pipenv install gunicorn==19.9.0
``` 
Nos regresamos al visual studio a modificar nuestro proyecto de django, nos vamos a la carpeta de config/settings.py . Y modificaremos lo siguiente :  
```   
ALLOWED_HOST  = [???*???] 
```  
Esto lo hacemos para que la aplicaci??n no marque error al intentar subir nuestro sitio a heroku <br>
Con esto hemos terminado los primeros pasos, ahora lo que resta es mandarlo a git. <br>
    
Iniciamos el proyecto de git 
``` 
git init 
``` 
Vemos los archivos si hay archivos ya agregados 
```     
git status
```     
En caso de que no agregamos con el par??metro ???A todos los elementos del directorio actual.
```     
git add ???A 
```     
Hacemos el commit mas un comentario para dar a conocer que hicimos en esta version
```     
git commit ???m ???Nuevas actualizaciones para el despliegue en Heroku???
```     
Lo mandamos a nuestro git hub para juntarlo con el proyecto
``` 
git push ???u origin master 
``` 
    
## Despliegue de Heroku 
Iniciamos sesi??n en nuestra cuenta de Heroku.
```
heroku login
```
Luego, ejecute el comando de creaci??n y Heroku creara aleatoriamente un nombre de aplicaci??n para usted.
``` 
heroku create 
``` 
Configure git para usar el nombre de su nueva aplicaci??n. 
```
heroku git:remote ???a nombre-proyecto-generado-1234
```
Le decimos a heroku que ignore los archivos est??ticos.
```
heroku config:set DISABLE_COLLECTSTATIC=1
```
Hacemos el push al master de heroku
```
git push heroku master
```
Cambiamos el proyecto a un modelo gratuito.
 ```
heroku ps:scale web=1  
```
# Proyecto  
Pagina web: https://djangoxblog.herokuapp.com/
