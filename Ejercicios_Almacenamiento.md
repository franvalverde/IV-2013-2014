Ejercicios Almacenamiento
=========================
Ejercicio 1
-----------
<strong>1. ¿Cómo tienes instalado tu disco duro? ¿Usas particiones? ¿Volúmenes lógicos?</strong>
<hr>
Con gparted podemos ver las particiones que tenemos en el disco duro.

![captura1] (https://dl.dropbox.com/s/b9e8szfrwlfwlod/gparted.png)

Las particiones son las siguientes:
- sda1 (EFI). En formato fat32 y contiene una interfaz que interactúa como puente entre el sistema operativo y el firmware base.
- sda2 (Macintosh). En formato hfs+, se trata de la partición del sistema operativo MacOs 10.8
- sda3 (Recovery HD). En formato hfs+, es la partición destinada para recuperar el sistema operativo MacOs en caso de error del sistema.
- sda4 (Ubuntu). En formato ext4, es la partición destinada para el sistema operativo Ubuntu 13.04 

<hr>
<strong>2. Si tienes acceso en tu escuela o facultad a un ordenador común para las prácticas, ¿qué almacenamiento físico utiliza?</strong>
<hr>

<hr>
<strong>3. Buscar ofertas SAN comerciales y comparar su precio con ofertas locales (en el propio ordenador) equivalentes.</strong>
<hr>


Ejercicio 2
-----------
<strong>Usar FUSE para acceder a recursos remotos como si fueran ficheros locales. Por ejemplo, sshfs para acceder a ficheros de una máquina virtual invitada o de la invitada al anfitrión.</strong>
<hr>

Arrancamos uno de los contenedor que hemos creado en otras sesiones con el comando:
<pre>
lxc-start -n contenedor
</pre>
Instalamos dentro del contenedor los siguientes paquetes
<pre>
sudo apt-get update
sudo apt-get install fuse
sudo apt-get install sshfs
</pre>
Agregamos el usuario al grupo de usuarios de fuse:
<pre>
sudo usermod -a -G fuse franvalverde
</pre>
Y por ultimo mapeamos la carpeta para poder usar el directorio del contenedor como si se tratara de un directorio local:
<pre>
sshfs ubuntu@10.0.3.45:/home/ubuntu/ /home/franvalverde/IV/carpetacontenedor
</pre>

Ejercicio 3
-----------
<strong>Crear imágenes con estos formatos (y otros que se encuentren tales como VMDK) y manipularlas a base de montarlas o con cualquier otra utilidad que se encuentre</strong>
<hr>


Ejercicio 4
-----------
<strong>Crear uno o varios sistema de ficheros en bucle usando un formato que no sea habitual (xfs o btrfs) y comparar las prestaciones de entrada/salida entre sí y entre ellos y el sistema de ficheros en el que se encuentra, para comprobar el overhead que se añade mediante este sistema</strong>
<hr>



Ejercicio 5
-----------
<strong>Instalar ceph en tu sistema operativo.</strong>
<hr>


Ejercicio 6
-----------
<strong>Crear un dispositivo ceph usando BTRFS o XFS</strong>
<hr>


Ejercicio 7
-----------
<strong>Almacenar objetos y ver la forma de almacenar directorios completos usando ceph y rados. </strong>
<hr>



Ejercicio 8
-----------
<strong>Tras crear la cuenta de Azure, instalar las herramientas de línea de órdenes (Command line interface, cli) del mismo y configurarlas con la cuenta Azure correspondiente</strong>
<hr>



Ejercicio 9
-----------
<strong>Crear varios contenedores en la cuenta usando la línea de órdenes para ficheros de diferente tipo y almacenar en ellos las imágenes en las que capturéis las pantallas donde se muestre lo que habéis hecho.</strong>
<hr>



Ejercicio 10
------------
<strong>Desde un programa en Ruby o en algún otro lenguaje, listar los blobs que hay en un contenedor, crear un fichero con la lista de los mismos y subirla al propio contenedor. Muy meta todo.</strong>
<hr>
