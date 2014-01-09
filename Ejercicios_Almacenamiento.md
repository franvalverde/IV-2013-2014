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
Los ordenadores que hay en la facultad, utilizan un sistema de ficheros remoto. Estan en formato NFS.

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
<i>RAW</i><br>Formato que evita los espacios sin asignar y que se representan por metadatos. Para crearlo realizamos lo siguiente:
<pre>
dd of=imagen.img bs=1k
</pre>
<i>qcow2</i><br>Formato usado por QEMU pero más adelante ha sido generalizado a casi todos los gestores de MVs de Linux. Para crealo realizamos lo siguiente:
<pre>
qemu-img create -f qcow2 imagen.qcow2 5M
</pre>
<i>vmdk</i><br>Formato de archivo utilizado por productos de VMware. Para crearlo realizamos lo siguiente:
<pre>
qemu-img create -f vmdk imagen.vmdk 5M
</pre>


Ejercicio 4
-----------
<strong>Crear uno o varios sistema de ficheros en bucle usando un formato que no sea habitual (xfs o btrfs) y comparar las prestaciones de entrada/salida entre sí y entre ellos y el sistema de ficheros en el que se encuentra, para comprobar el overhead que se añade mediante este sistema</strong>
<hr>
Creamos la imagen con qemu como en el ejercicio 3.
<pre>
qemu-img create -f raw ej4.img 512M
</pre>
Usamos losetup que se utiliza para asociar dispositivos bucle con archivos regulares o bloque de dispositivos, para separar los dispositivos loop y para consultar el estado de un dispositivo loop.
<pre>
sudo losetup -v -f xfs.img
</pre>
Le damos formato:
<pre>
sudo mkfs.xfs /dev/loop3
</pre>
Y por ultimo montamos:
<pre>
sudo mount /dev/loop3 /mnt/loop3/
</pre>

Ejercicio 5
-----------
<strong>Instalar ceph en tu sistema operativo.</strong>
<hr>
<pre>
sudo apt-get install ceph-mds
</pre>

Ejercicio 6
-----------
<strong>Crear un dispositivo ceph usando BTRFS o XFS</strong>
<hr>
En primer lugar creamos la imagen de ceph y se le da formato a la imagen para que tenga un sistema de archivos:
<pre>
qemu-img create -f raw imagen.img 512M
sudo mkfs.xfs /dev/loop2
</pre>
Arrancamos el demonio:
<pre>
sudo /etc/init.d/ceph -a start
</pre>
Y por ultimo montamos:
<pre>
sudo mount -t ceph ubuntu:/ /mnt/ceph
</pre>


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
