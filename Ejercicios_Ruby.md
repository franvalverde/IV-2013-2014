Ejercicios Ruby
===============
Ejercicio 1
-----------
<strong>Instalar Ruby y usar</strong>
<hr>
<pre>
sudo apt-get install ruby
</pre>
Ejercicio 2
-----------
<strong>Crear un programa en Ruby que imprima los números desde el 1 hasta otro contenido en una variable.</strong>
<hr>
[!Captura1](https://dl.dropbox.com/s/tivnqy0hc4uyfg2/primerprogramaRUBY.png)

Ejercicio 3
-----------
<strong>¿Se pueden crear estructuras de datos mixtas en Ruby? Crear un array de hashes de arrays e imprimirlo.</strong>
<hr>
Si.
<pre>
#!/usr/bin/ruby

datos = { :nombre => 'francisco',
  :apellidos => ['valverde','villalba'],
  :telefonos => [62036112,95770012] }
puts datos.inspect
</pre>

Ejercicio 4
-----------
<strong>Crear una serie de funciones instanciadas con un URL que devuelvan algún tipo de información sobre el mismo: fecha de última modificación, por ejemplo. Pista: esa información está en la cabecera HTTP que devuelve</strong>
<hr>

