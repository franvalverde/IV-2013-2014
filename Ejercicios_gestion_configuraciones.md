Ejercicios Gestión de Configuraciones
=====================================
Ejercicio 1
-----------
<strong>Instalar chef en la máquina virtual que vayamos a usar</strong><hr>
Chef es una herramienta para la gestión de configuraciones. Es decir, se encarga de instalar y configurar las aplicaciones en servidores o incluso estaciones de trabajo. Con él podemos realizar desde configuraciones básicas como establecer la hora del sistema, el idioma… hasta cosas tan complejas como levantar y configurar un cluster entero.

En una máquina tipo ubuntu, la forma más sencilla es usando el paquete Omnibus proporcionado por Opscode:
<pre>
wget -O- https://www.opscode.com/chef/install.sh | sudo bash
</pre>

Ejercicio 2
-----------
<strong>Crear una receta para instalar nginx, tu editor favorito y algún directorio y fichero que uses de forma habitual.</strong><hr>
Creamos un fichero ruby con el nombre que prefiramos, en mi caso ejercicio2.rb, y añadimos la información necesaria para realizar nuestra receta.
Comenzaremos con la creación de un directorio y un fichero, dentro de nuestra receta ejercicio2.rb añadimos lo siguiente:
<pre>
directory 'carpeta/'
file "carpeta/receta" do
  owner "franvalverde"
  group "franvalverde"
  mode 00777
  action :create
  content "Creado desde receta "
end
</pre>
Para ejecutarlo usamos `chef-apply ejercicio2.rb`. Este es el resultado:

![captura1](https://dl.dropbox.com/s/ksb0iojg0bdsovx/receta_carpeta.png)

Añadiremos ahora lo necesario para instalar nginx y un editor, por ejemplo geany. 
<pre>
package 'nginx' //esto internamente hara un apt-get install
package 'geany'
</pre>
![captura2](https://dl.dropbox.com/s/41cr4qsl6zqv72w/receta_geany.png)

Ejercicio 3
-----------
<srong>Escribir en YAML la siguiente estructura de datos en JSON</strong><hr>
YAML es un formato de serialización de datos legible por humanos inspirado en lenguajes como XML, C, Python y Perl.
<pre>
uno:"dos"
tres:
    -4
    -5
    -"Seis"
    -
        -siete:8
        -nueve:[10,11]
</pre>

Ejercicio 4 
-----------
<strong>Desplegar los fuentes de la aplicación de DAI, usando ansible</strong>
<hr>
Ansible es sistema de gestión remota de configuración que permite gestionar simultáneamente miles de sistemas diferentes. Está basado en YAML para la descripción de los sistemas y escrito en Python.
Nos descargamos e instalamos en primer lugar ansible:
<pre>
sudo pip install ansible
</pre>
Creamos un archivo donde le indicaremos donde se encuentra alojada nuestra aplicación, en él introducimos lo siguiente:
<pre>
[azure]
ubuntu1204peq.cloudapp.net/ingenia/
</pre>
Creamos una variable local que va a usar ansible para realizar la conexión, en ella introduce la dirección a nuestro archivo con los servidores de azure. Y posteriormente realizamos un ping para comprobar que se ha realizado la conexión correctamente.

![captura_ansible1](https://dl.dropbox.com/s/kmwr3e9rs0bu4d9/ansible_azure.png)

Podemos clonar un repositorio con ansible de forma muy sencilla:
<pre>
ansible azure -m git -a "repo=https://github.com/IV-GII/Ingenia.git dest=~/ansible_ingenia vesion=HEAD" -vvvv
</pre>

Ejercicio 5 
-----------
<strong>Desplegar la aplicación de DAI con todos los módulos necesarios usando un playbook de Ansible</strong>
...

Ejercicio 6
-----------
<strong>Instalar una máquina virtual Debian usando Vagrant y conectar con ella.</strong><hr>
La ventaja de Vagrant es que permite gestionar el ciclo de vida completo de una máquina virtual, desde la creación hasta su destrucción pasando por el provisionamiento y la monitorización o conexión con la misma. 
<pre>
sudo apt-get install Vagrant
</pre>
Nos descargamos una distribución debian:
<pre>
vagrant box add debian https://dl.dropboxusercontent.com/u/197673519/debian-7.2.0.box
</pre>

![captura_vagrant1](https://dl.dropbox.com/s/oejm260fl1kaguj/vagrant.png)


Crea un fichero Vagrantfile (y así te lo dice) que permite trabajar y llevar a cabo cualquier configuración adicional. Una vez hecho eso ya podemos inicializar la máquina y trabajar con ella.

<pre>
vagrant init debian
vagrant up
vagrant ssh
</pre>

Ejercicio 7
-----------
<strong>Crear un script para provisionar nginx o cualquier otro servidor web que pueda ser útil para alguna otra práctica</strong><hr>

Ejercicio 8
-----------
<strong>Configurar tu máquina virtual usando vagrant con el provisionador ansible</strong><hr>
