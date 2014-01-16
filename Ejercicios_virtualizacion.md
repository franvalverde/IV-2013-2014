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
![captura2](https://dl.dropbox.com/s/20r4r1szu0lrln0/kvm_Imagen.png)

Una vez que se termina la instalación, solo falta "encender" la máquina virtual que ya se ha instalado, ¿Cómo hacer esto? Sencillo, debemos ejecutar el siguiente comando:

qemu -hda NOMBRE.img -m 256 -boot c

<hr>
<strong>2. Hacer un ejercicio equivalente usando otro hipervisor como Xen, VirtualBox o Parallels.</strong>
<hr>
Realizamos la instalación en Parallels.<br>
1. Adquirimos Parallels (descargamos la versión de prueba).<br>2. Descargamos la Iso en live CD / DVD para la distribución deseada

3. Iniciamos Parallels

4. Pulsamos el + en Máquinas Virtuales Parallels o tambien podemos hacer clic en Archivo | Nuevo ... en el menú

5. Buscamos el archivo iso. En Instalar desde desplegables (seleccione Elegir un archivo de imagen ... para abrir un diálogo de archivo)

6. Parallels intentará 'auto-detectar' el sistema operativo. Si falla, lo podemos seleccionar en el menú desplegable donde aparecen las distribuciones más populares, y siempre se puede elegir otro Linux Kernel 2.6 (esto funciona incluso si la distribucion utiliza Linux 3.0.x)

7. Continuar con la instalación, de igual forma que cuando se hace una instalación tipica.

8. Una vez terminada aparecerá nuestra maquina para poder ser arrancada.
