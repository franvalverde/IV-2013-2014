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

El usuario y contraseña serian 'root', 'password'


Ejercicio 4
-----------



Ejercicio 5
-----------



Ejercicio 6
-----------


Ejercicio 1
-----------


[Ejercicios del 11 noviembre] (https://github.com/franvalverde/IV-2013-2014/wiki/Ejercicios-11-noviembre-2013)

[Ejercicios del 15 noviembre] (https://github.com/franvalverde/IV-2013-2014/wiki/Ejercicios-15-noviembre-2013)

[Ejercicios del 22 noviembre] (https://github.com/franvalverde/IV-2013-2014/wiki/Ejercicios-22-noviembre-2013)

[Ejercicios del 25 noviembre] (https://github.com/franvalverde/IV-2013-2014/wiki/Ejercicios-25-noviembre-2013)
