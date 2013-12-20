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
