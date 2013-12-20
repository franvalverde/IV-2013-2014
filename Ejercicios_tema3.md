Ejercicios Tema 3 IV 2013-2014
==============================
Ejercicio 1
-----------
<strong>Instala LXC</strong>
<hr>
Actualizamos los repositorios de apt e instalamos lxc. 
<pre>
sudo apt-get install lxc
</pre>
Ejercicio 2
-----------
<strong>Comprobar que interfaces puente se han creado y explicarlos</strong>
<hr>
En primer lugar creamos el contenedor:
<pre>
sudo lxc-create -t ubuntu -n contenedor
</pre>
Despues de una larga instalación donde descomprime, valida y configura todos los paquetes para el contenedor, ejecutamos nuestro contenedor.

![captura 1] (https://dl.dropbox.com/s/r95d3sfhqz7i107/contenedor_instalado.png)

<pre>
sudo lxc-start -n contenedor
</pre>
Arracamos el contenedor y nos pide usuario y contraseña (ubuntu, ubuntu).
Para ver las interfaces, ejecutamos ifconfig.

![captura 2] (https://dl.dropbox.com/s/i3idzerntqxgorh/ifconfig_contenedor.png)

Ejercicio 3
-----------
<strong>1. Crear y ejecutar un contenedor basado en Debian.</strong>
<hr>
<pre>
sudo lxc-create -t ubuntu -n contenedor
</pre>
Despues de una larga instalación donde descomprime, valida y configura todos los paquetes para el contenedor, ejecutamos nuestro contenedor.

![captura 3] (https://dl.dropbox.com/s/r95d3sfhqz7i107/contenedor_instalado.png)

<pre>
sudo lxc-start -n contenedor
</pre>
Arracamos el contenedor y nos pide usuario y contraseña (ubuntu, ubuntu).

<hr>
<strong>2. Crear y ejecutar un contenedor basado en otra distribución, tal como Fedora.</strong>
<hr>

He elegido un contenedor basado en CentOS. Para instalar centos debemos tener ciertos paquetes como:
<pre>
- librpm3 librpmbuild3 librpmio3 librpmsign1 libsqlite0 
- python-rpm python-sqlite python-sqlitecachec python-support python-urlgrabber 
- rpm rpm-common rpm2cpio 
- yum 
- debootstrap 
- bridge-utils
</pre>
Para ello actualizamos los repositorios de apt-get e instalamos cada uno de estos paquetes.
Para realizar la instalación:
<pre>
sudo lxc-install -t centos -n contenedor-centos
</pre>
Una vez terminada la instalación accedemos al contenedor.
<pre>
sudo lxc-start -n contenedor-centos
</pre>

![captura 4] (https://dl.dropbox.com/s/ra8b8mf7fno2fu0/arranque_centos_contenedor.png)

El usuario y contraseña serian `root`, `password`


Ejercicio 4
-----------

<strong>1. Instalar lxc-webpanel y usarlo para arrancar, parar y visualizar las máquinas virtuales que se tengan instaladas.</strong>
<hr>
Para instalar lxc-webpanel seguimos este tutorial [http://lxc-webpanel.github.io/install.html] donde lo primero que nos indica es que usando la herramienta wget obtengamos el script para instalar el webpanel de lxc.
<pre>
wget http://lxc-webpanel.github.io/tools/install.sh -O - | bash
</pre>
Si por algún motivo la instalación no se completa esta la opción de realizar la instalación manual que se basa en clonar un repositorio de github y lanzar el archivo python de esa carpeta para ejecutar el proceso.

Para comprobar que funciona entramos en http://localhost:5000 y acceder con el usuario admin y contraseña admin.

![captura 5] (https://dl.dropbox.com/s/ddk7rjlqb6aj0jl/lwc%20web%20panel%20login.png)

<hr>
<strong>2. Desde el panel restringir los recursos que pueden usar: CPU shares, CPUs que se pueden usar (en sistemas multinúcleo) o cantidad de memoria.</strong>
<hr>

Seleccionamos el contenedor al que vamos a realizarle la restricción, en mi caso se lo haré al contenedor "quemestascontainer". Hay que tener en cuenta que el contenedor debe estar parado para modificar estos aspectos, en caso contrario nos mostrará el error "Internal Server Error".

Modificaciones: 
- memory limit 1024
- memory + SWAP limit 1024
- CPUs 1
- CPU shares 512

Ejercicio 5
-----------
<strong>Comparar las prestaciones de un servidor web en una jaula y el mismo servidor en un contenedor. Usar nginx.</strong>
<hr>
Usaremos la jaula creada en el tema anterior "debian" para arrancarla:
<pre>
sudo chroot debian
</pre>
Y el contenedor ubuntu, para lanzarlo:
<pre>
sudo lxc-start -n contenedor
</pre>
Instalamos nginx en ambas plataformas:
<pre>
sudo apt-get update
sudo apt-get install nginx
sudo apt-get install apache2-utils
# en caso de la jaula no es necesario poner sudo ya que accedemos como tal.
</pre>
- Asignamos una ip fija al contenedor mediante lxc-panel control.
- Montamos el filesystem virtual /proc en la jaula "mount -t proc proc /proc"
- Arrancamos nginx: "/etc/init.d/nginx start"

<u>Contenedor</u>

ab -n 100 -c 10 http://10.0.3.63/

![captura 6] (https://dl.dropbox.com/s/hyvy6yjj9n6jx89/ab-contenedor.png)

<u>Jaula</u>

ab -n 100 -c 10 http://127.0.0.1/

![captura 7] (https://dl.dropbox.com/s/f8iciidfqwsbodf/ab-jaula.png)

Ejercicio 6
-----------



Ejercicio 1
-----------


[Ejercicios del 11 noviembre] (https://github.com/franvalverde/IV-2013-2014/wiki/Ejercicios-11-noviembre-2013)

[Ejercicios del 15 noviembre] (https://github.com/franvalverde/IV-2013-2014/wiki/Ejercicios-15-noviembre-2013)

[Ejercicios del 22 noviembre] (https://github.com/franvalverde/IV-2013-2014/wiki/Ejercicios-22-noviembre-2013)

[Ejercicios del 25 noviembre] (https://github.com/franvalverde/IV-2013-2014/wiki/Ejercicios-25-noviembre-2013)
