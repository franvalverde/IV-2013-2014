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
Nos descargamos e instalamos en primer lugar ansible:
<pre>
sudo pip install ansible
</pre>
Creamos un archivo donde le indicaremos donde se encuentra alojada nuestra aplicación, en él introducimos lo siguiente:
<pre>
[azure]
http://ubuntu1204peq.cloudapp.net/ingenia/
</pre>
