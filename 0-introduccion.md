# Primeros pasos

La idea de este libro es que vayas siguiendo las instrucciones y las vayas ejecutando en tu computador. Vas a necesitar tener instalado Ruby y un editor de texto como [Atom](https://atom.io/), [Sublime Text](https://www.sublimetext.com/), o el de tu preferencia.

Voy a asumir que ya tienes Ruby instalado. Puedes verificar abriendo una línea de comandos y ejecutando `ruby -v`. Te debería aparecer una línea similar a la siguiente:

```shell
$ ruby -v
ruby 2.3.0p0 (2015-12-25 revision 53290) [x86_64-darwin13]
```

La versión puede ser diferente, cualquier versión mayor a 2.1.0 funciona.

Si ves un mensaje diciendo que el comando no fue encontrado, significa que aún no tienes Ruby instalado. Si estás en Windows puedes seguir las instrucciones en el siguiente video:

* [Instalación de Ruby en Windows](https://makeitreal.wistia.com/medias/s3dvclbol2)

## IRB

Existen dos formas de ejecutar código Ruby. La primera es abrir el interpretador de Ruby ejecutando el comando IRB.

```shell
$ irb
2.3.0 :001 >
```

El interpretador nos permite escribir cualquier expresión válida de Ruby y oprimir `Enter`. El interpretador evalúa la expresión y debajo muestra el resultado:

```shell
$ irb
2.3.0 :001 > 1 + 2
  => 3
2.3.0 :002 >
```

Puedes repetir ese mismo proceso las veces que quieras. Esa es una forma muy rápido de probar código. Para salir escribe `exit` y oprime `Enter`.

## Nuestro primer programa

La otra forma de ejecutar código Ruby es crear un archivo con extensión `rb` en el que escribimos nuestro código. Para eso crea una carpeta en tu máquina y úbicate sobre ella en la consola. Ábrela con tu editor preferido.

Crea un archivo llamado `hello_world.rb` (los archivos de Ruby terminan con la extensión `rb` y se recomienda nombrar el archivo todo en minúscula separando las palabras con raya al piso). En el archivo escribe lo siguiente:

```ruby
puts "Hola mundo"
```

Guárdalo. Para ejecutarlo escribe lo siguiente en la consola (asegúrate de estar sobre la carpeta donde está el archivo):

```shell
$ ruby hello_world.rb
Hola mundo
```

Deberías ver la cadena de texto "Hola mundo" en la consola. Cambia el texto por cualquier otro y vuelve a ejecutar el archivo.

¡Felicitaciones, has creado tu primer programa en Ruby!

## Errores

Veamos ahora qué pasa si cometemos algún error en nuestro código. Por ejemplo, borra el caracter `u` de la palabra `puts` y vuelve a ejecutar el archivo:

```shell
$ ruby hello_world.rb
hello_world.rb:1:in `<main>`: undefined method `pts` for main:Object (NoMethodError)
Did you mean? puts
```

El error nos dice que ocurrió en el archivo `hello_world.rb` en la línea `1`, y que no se encuentra el método `pts`. Además nos da una sugerencia (correcta en este caso) preguntándonos si nos estábamos refiriendo al método `puts`.

Hay veces en los que es fácil encontrar los errores, otras veces no es tan fácil. Lo que si es cierto es que a medida que vayas trabajando con el lenguaje vas a ir desarrollando una intuición que te va a permitir solucionar los errores más fácilmente, pero al principio es un proceso lento que es parte de ese aprendizaje.

Vamos a ocasionar otro error, vuelve a escribir `puts` correctamente, pero ahora borra la comilla al final de esa lína y vuelve a ejecutar el archivo. Debería salir un mensaje como el siguiente:

```shell
$ ruby hello_world.rb
hello_world.rb:1: unterminated string meets end of file
```

Esta vez nos dice que hay una cadena de texto que no está terminada y se encuentra con el final del archivo, o se alarga hasta el final del archivo.

Vuelve a agregar la comilla y verifica que se ejecute normalmente.

Ruby ejecuta el archivo línea por línea, una después de la otra. Así que podemos agregar otra segunda línea:

```ruby
puts "Hola mundo"
puts "Esto está muy bacano"
```

El comando `puts` se utiliza para imprimir una cadena de texto en la consola y al final de cada cadena de texto agrega un salto de línea (un Enter). Si no quieres que agregue ese salto de línea al final utiliza `print` en vez de `puts`.

```ruby
print "Hola mundo"
print "Esto está muy bacano"
```

Si lo ejecutamos

```shell
$ ruby hello_world.rb
Hola mundoEsto está muy bacano
```

Aparecen las dos cadenas en una misma línea. El print lo vamos a usar más adelante. Por ahora vuelve a cambiarlo por `puts`.

## Comillas sencillas o dobles

Ahora cambia las comillas de la segunda línea por comillas sencillas:

```ruby
puts "Hola mundo"
puts 'Esto está muy bacano'
```

Ejecuta el archivo y fíjate que el resultado permanezca igual:

```shell
$ ruby hello_world.rb
Hola mundo
Esto está muy bacano
```

No importa cuáles comillas utilices (aunque más adelante vamos a ver casos en que solo podemos utilizar las comillas dobles). Si el texto contiene comillas simples utiliza comillas dobles; si el texto contiene comillas dobles utiliza comillas sencillas:

```ruby
puts "Hol'a mundo"
puts 'Esto está muy "bacano"'
```

Si ejecutas de nuevo el archivo deberían aparecer esas comillas dentro del texto:

```shell
$ ruby hello_world.rb
Hol'a mund'o
Esto está muy "bacano"
```

Agreguemos una línea más a nuestro archivo:

```ruby
puts "Hol'a mundo"
puts 'Esto está muy "bacano"'
puts "puts 'hola mundo'"
```

Fíjate que esa última línea contiene código Ruby, pero como está dentro de una cadena de texto Ruby ignora lo que está allí adentro y lo muestra tal y como lo escribimos:

```shell
$ ruby hello_world.rb
Hol'a mund'o
Esto está muy "bacano"
puts 'hola mundo'
```

## Comentarios

Los comentarios se utilizan para documentar o aclarar nuestro código. Para agregar un comentario se utiliza el caracter `#`:

```ruby
# este es un comentario
puts "Hol'a mundo"
puts 'Esto está muy "bacano"'
puts "puts 'hola mundo'" # este es un comentario
```

En este caso hemos agregado dos comentarios: el de la primera línea y el que está al final del último `puts`. Los comentarios son ignorados por Ruby así que deberías ver el mismo resultado que antes cuando ejecutes el archivo.

Agreguemos un nuevo comentario:

```ruby
# este es un comentario
# puts 'hola mundo'
puts "Hol'a mundo"
puts 'Esto está muy "bacano"'
puts "puts 'hola mundo'" # este es un comentario
```

Fíjate que en el nuevo comentario estamos escribiendo código Ruby válido, pero por estar en un comentario Ruby lo ignora completamente.

## Matemáticas

Crea un nuevo archivo llamado `math.rb` con el siguiente código:

```ruby
puts 1 + 2
puts 3 * 4 + 5
puts 8 / 2
```

Ejecuta el archivo, deberías ver algo como lo siguiente:

```shell
$ ruby math.rb
3
17
4
```

El segundo ejemplo es particularmente interesante. Ruby sigue el mismo estandar que en matemáticas, y por lo tanto la multiplicación se ejecuta primero que la suma. Puedes cambiar el comportamiento con paréntesis, cambia la operación de la segunda línea por `3 * (4 + 5)`. El resultado debería ser `27`.

## Interpolación

Modifica el archivo con el siguiente código (le agregamos los `print` antes de cada operación):

```ruby
print "1 + 2 = "
puts 1 + 2
print "3 * 4 + 5 = "
puts 3 * 4 + 5
print "8 / 2 = "
puts 8 / 2
```

Si ejecutas el archivo nuevamente deberías ver lo siguiente:

```shell
$ ruby math.rb
1 + 2 = 3
3 * 4 + 5 = 17
8 / 2 = 4
```

Sin embargo, podemos hacer nuestro programa más corto con interpolación:

```ruby
puts "1 + 2 = #{1 + 2}"
puts "3 * 4 + 5 = #{3 * 4 + 5}"
puts "8 / 2 = #{8 / 2}"
```

Ejecuta el archivo, deberías ver el mismo resultado que antes.

La interpolación nos permite evaluar código Ruby dentro de una cadena de texto. La sintaxis que debes utilizar es `#{}` y lo que deseas evaluar va dentro de los corchetes.

**Nota:** Para utilizar interpolación es necesario utilizar comillas dobles en vez de simples.

## Comparaciones

Crea un nuevo archivo llamado `comparison.rb` y escribe lo siguiente:

```ruby
puts 5 > 3 # mayor que
puts 5 >= 3 # mayor o igual que
puts 4 < 4 # menor que
puts 4 <= 4 # menor o igual que
puts 2 == 2 # igual a
puts 2 != 2 # diferente de
```

Ejecuta el archivo, deberías ver algo así:

```shell
$ ruby comparisons.rb
true
true
false
true
true
false
```

Cómo ejercicio, agrégales un texto como lo hicimos con las operaciones matemáticas utilizando interpolación para que aparezca así:

```shell
$ ruby comparisons.rb
5 > 3 es true
5 >= 3 es true
4 < 4 es false
4 <= 4 es true
2 == 2 es true
2 != 2 es false
```
