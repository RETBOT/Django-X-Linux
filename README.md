# Curso Practico de Django desde Sistemas Operativos GNU Linux
En este repositorio iremos viendo todo lo necesario para la instalacion de los elementos necesarios 


# Instalacion del Sistema Operativo
Para este taller se usara el Sistema operativo Fedora 36
<div align="center"> 
<img src="https://github.com/IGerardoJR/testImages/raw/main/ImagenesGit/Fedora-logo.png" width="300" height="360" ></img>
</div>

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
  
    
    
