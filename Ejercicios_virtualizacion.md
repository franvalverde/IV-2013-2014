Ejercicios de Virtualización
============================
Ejercicio 1
-----------
<strong>Instalar los paquetes necesarios para usar KVM</strong>
<hr>
<pre>
sudo apt-get install qemu-kvm 
sudo apt-get install qemu-system 
</pre>

Ejercicio 2
-----------
<strong>1. Crear varias máquinas virtuales con algún sistema operativo libre, Linux o BSD</strong><hr>
Dado que KVM es un módulo del kernel, puede que no esté cargado por defecto. Dependiendo del procesador que usemos, lo cargamos con:
<pre>
sudo modprobe kvm-amd
o
sudo modprobe kvm-intel
</pre>
Nosotros debemos primeramente crear la imagen donde queremos que se vaya a instalar el sistema operativo. La única propiedad que es necesaria para crear la imagen es el tamaño de esta, debemos especificar el tamaño que ocupará esa imagen. Para crear la imagen: 
![captura1](https://dl.dropbox.com/s/20r4r1szu0lrln0/kvm_Imagen.png)

Una vez creada la imagen ya podemos empezar a instalar el sistema operativo. En el mismo directorio donde creamos la imagen debemos ejecutar lo siguiente: 
![captura2](https://dl.dropbox.com/s/qcx9rpgkt3ftn3y/slitaz.png)

He instalado slitaz (slitaz.img) y Minino (maquina.img).

Una vez que se termina la instalación, solo falta "encender" la máquina virtual que ya se ha instalado, ¿Cómo hacer esto? Sencillo, debemos ejecutar el siguiente comando:

<pre>
qemu -hda maquina.img -m 256 -boot c
</pre>

<hr>
<strong>2. Hacer un ejercicio equivalente usando otro hipervisor como Xen, VirtualBox o Parallels.</strong>
<hr>
Realizamos la instalación en Parallels.<br>
1. Adquirimos Parallels (descargamos la versión de prueba).<br>2. Descargamos la Iso en live CD / DVD para la distribución deseada<br>3. Iniciamos Parallels<br>4. Pulsamos el + en Máquinas Virtuales Parallels o tambien podemos hacer clic en Archivo | Nuevo ... en el menú<br>5. Buscamos el archivo iso. En Instalar desde desplegables (seleccione Elegir un archivo de imagen ... para abrir un diálogo de archivo)<br>6. Parallels intentará 'auto-detectar' el sistema operativo. Si falla, lo podemos seleccionar en el menú desplegable donde aparecen las distribuciones más populares, y siempre se puede elegir otro Linux Kernel 2.6 (esto funciona incluso si la distribucion utiliza Linux 3.0.x)<br>

![captura3](https://dl.dropbox.com/s/8ic5ihatayzuth9/parallels1.png)

Continuar con la instalación, de igual forma que cuando se hace una instalación tipica.
Una vez terminada aparecerá nuestra maquina para poder ser arrancada.

![captura4](https://dl.dropbox.com/s/zyrgb4i13tt7tdf/parallels2.png)

Ejercicio 3
-----------
<strong>Crear un benchmark de velocidad de entrada salida y comprobar la diferencia entre usar paravirtualización y arrancar la máquina virtual</strong>
<hr>
...

Ejercicio 4
-----------
<strong>Crear una máquina virtual Linux con 512 megas de RAM y entorno gráfico LXDE a la que se pueda acceder mediante VNC y ssh</strong>
<hr>
Creamos la imagen:
<pre>
qemu-img create kvm/mint.img 8G //linux mint exige minimo 8gb
</pre>
Lanzamos la instalación con la opcion -m 512
<pre>
qemu -hda kvm/mint.img -cdrom /home/franvalverde/Descargas/linuxmind-16-kde.iso -boot d -m 512
</pre>
...

Ejercicio 5
-----------
<strongCrear una máquina virtual ubuntu e instalar en ella un servidor nginx para poder acceder mediante web.</strong><hr>
Creamos la imagen:
<pre>
qemu-img create kvm/ubuntu.img 8G
</pre>
Lanzamos la instalación
<pre>
qemu -hda kvm/ubuntu.img -cdrom /home/franvalverde/Descargas/ubuntu-13.04-desktop-amd64.iso -boot d
</pre>
Una vez instalada la ejecutamos con:
<pre>
qemu -hda ubuntu.img -m 1G -boot c
</pre>
Instalamos nginx:
<pre>
sudo apt-get install nginx
</pre>
Lanzamos el demonio:

![ejercicio5cap1](https://dl.dropbox.com/s/mem45i2e8xl5vwc/nginx-ubuntu.png)

Comprobamos que podemos acceder via web a nuestra maquina:

![ejercicio5cap2](https://dl.dropbox.com/s/6jfxsnfwqq2ho0s/nginx-ubuntu2.png)

Ejercicio 6
-----------
<strong>Usar juju para hacer el ejercicio anterior.</strong><hr>
- <i>CONFIGURACIÓN PREVIA</i><br>
En primer lugar instalamos juju en el caso de no tenerlo instalado ya.
<pre>
sudo add-apt-get-repository ppa:juju/stable
sudo apt-get update
sudo apt-get install juju-core
# creamos el archivo de configuración
juju init
</pre>
Modificamos el archivo de configuración que como nos indica el terminal al crearlo esta en la ruta `~/.juju/environments.yaml`.
Es importante modificar la linea de default para que trabaje en entorno local:
<pre>
#default: amazon
default: local
</pre>
Creamos el entorno:
<pre>
juju bootstrap
</pre>
- <i>CONFIGURACIÓN AZURE</i><br>
Primero nos creamos un certificado rellenando todos los datos:
<pre>
openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -keyout azure.pem -out azure.pem
openssl x509 -inform pem -in azure.pem -outform der -out azure.cer
chmod 600 azure.cer
</pre>
Cargamos en la web azure el certificado que acabamos de crear:

![ejer6-cap1](https://dl.dropbox.com/s/a198zj1natry1t6/certificado_Azure.png)

Modificamos el archivo de configuración de juju en el apartado de azure ponemos la información relevante a nuestro usuario de azure.

![ejer6-cap2](https://dl.dropbox.com/s/mzfgdp4rbarnnma/configuracionAzureYaml.png)


Ejercicio 7
-----------
<strong>Instalar una máquina virtual Ubuntu 12.04 para el hipervisor que tengas instalado.</strong><hr>
...

