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
<hr>
<strong>2. Hacer un ejercicio equivalente usando otro hipervisor como Xen, VirtualBox o Parallels.</strong><hr>
