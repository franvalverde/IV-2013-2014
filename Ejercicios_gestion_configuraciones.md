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
Para ejecutarlo usamos `chef-aply ejercicio2.rb`. Este es el resultado:

![captura1](https://dl.dropbox.com/s/ksb0iojg0bdsovx/receta_carpeta.png)

