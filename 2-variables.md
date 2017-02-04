# Variables y entrada del usuario

Las variables nos permiten almacenar información temporal que podemos usar más adelante en nuestros programas.

Crea un archivo llamado `variables.rb` y agrega lo siguiente:

```ruby
name = "Germán" # cámbialo por tu nombre
puts "Hola #{name}"
```

Ejecúta el archivo y verifica que el resultado sea el correcto:

```shell
$ ruby variables.rb
Hola Germán
```

En este ejemplo estamos definiendo una variable con nombre `name` y le asignamos el valor "Germán" (o el valor que le hayas asignado). En la siguiente línea estamos utilizando interpolación para mostrar la cadena de texto "Hola " seguido del valor que tenga en ese momento la variable `name`.

Si no interpolamos la variable simplemente veríamos "Hola name" en la pantalla.

Bien, crea ahora un archivo llamado `square.rb` y agrega el siguiente código:

```ruby
puts "El perímetro de un cuadrado de lado 5 es #{5 * 4}"
puts "El área de un cuadrado de lado 5 es #{5 * 5}"
```

Si lo ejecutamos te debería aparecer lo siguiente:

```shell
$ ruby square.rb
El perímetro de un cuadrado de lado 5 es 20
El área de un cuadrado de lado 5 es 25
```

El problema con este código es que si quisiéramos ahora calcular otros tamaños, nos tocaría modificar ese valor en varias partes del código. Mejoremos ese código para que utilice una variable:

```ruby
side = 5

puts "El perímetro de un cuadrado de lado #{side} es #{side * 4}"
puts "El área de un cuadrado de lado #{side} es #{side * side}"
```

Si ejecutas el código te debería dar el mismo resultado. La ventaja es que si quieres calcular el perímetro y el área de un cuadrado con otro tamaño solo debes cambiar el valor de la variable. Intenta con 18 (te debería dar 72 de perímetro y 324 de área) y después con 39.

## Entrada del usuario

A través de la consola es posible pedirle al usuario que ingrese uno o varios valores que podemos utilizar en nuestros programas. Para esto crea un archivo llamado `input.rb` y agrega lo siguiente:

```ruby
print "Ingresa tu nombre: "
name = gets.chomp
puts "Hola #{name}"
```

Al ejecutarlo, el programa te debería pedir que ingreses tu nombre y te debería saludar:

```shell
$ ruby input.rb
Ingresa tu nombre: Germán
Hola Germán
```

Lo más importante de este código es la línea `name = gets.chomp` que le pide información al usuario y la almacena en la variable `name`.

Con este conocimiento podemos mejorar el programa que calcula el perímetro y el área de un cuadrado:

```ruby
print "Ingresa la longitud del lado del cuadrado: "
side = gets.chomp

puts "El perímetro de un cuadrado de lado #{side} es #{side * 4}"
puts "El área de un cuadrado de lado #{side} es #{side * side}"
```

Si ejecutas este código te debería aparecer lo siguiente:

```shell
$ ruby square.rb
Ingresa la longitud del lado del cuadrado: 5
El perímetro de un cuadrado de lado 5 es 5555
square.rb:5:in ''*': no implicit conversion of String into Integer (TypeError)
	from square.rb:5:in `<main>'
```

Tenemos dos problemas. El primero es que está calculando mal el perímetro del cuadrado (5555 en vez de 20). El otro es que sale un error diciendo que no se puede hacer una conversión implícita de una cadena de texto a un número (entero). La razón es que cuando capturamos la información del usuario Ruby asume que es una cadena de texto, así que tenemos que hacer un cambio en nuestro código para que funcione:

```ruby
print "Ingresa la longitud del lado del cuadrado: "
side = gets.chomp.to_i

puts "El perímetro de un cuadrado de lado #{side} es #{side * 4}"
puts "El área de un cuadrado de lado #{side} es #{side * side}"
```

¿Notas el cambio? En la segunda línea le agregamos `.to_i` al final para convertir lo que ingrese el usuario a un número (integer). Ahora, si probamos nuevamente debería funcionar:

```shell
$ ruby square.rb
Ingresa la longitud del lado del cuadrado: 5
El perímetro de un cuadrado de lado 5 es 20
El área de un cuadrado de lado 5 es 25
```
