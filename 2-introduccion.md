# Primeros pasos

En este capítulo vas a aprender a ejecutar código Ruby. Nuestra recomendación es que transcribas y ejecutes cada uno de los ejemplos de este libro en tu computador e intentes solucionar cada uno de los ejercicios de forma que aceleres tu aprendizaje. Recuerda que la mejor forma de aprender sobre programación es escribiendo código.

## Instalación de Ruby

Antes de instalar Ruby verifica si lo tienes instalado abriendo una línea de comandos y ejecutando `ruby -v`. Si ya lo tienes te va a aparecer una línea similar a la siguiente:

```
$ ruby -v
ruby 2.3.0p0 (2015-12-25 revision 53290) [x86_64-darwin13]
```

La versión puede ser diferente, cualquier versión mayor a 2.1.0 está bien.

Si ves un mensaje diciendo que el comando no fue encontrado, significa que aún no tienes Ruby instalado. Puedes encontrar las instrucciones para instalarlo en el siguiente enlace: https://github.com/makeitrealcamp/ruby-installation.

Una vez que tengas instalado [Ruby](https://ruby-lang.org/) y lo hayas verificado, continúa. En las siguientes secciones vamos a ver cómo ejecutar código Ruby en el interpretador y desde un archivo.

## IRB

Existen dos formas de ejecutar código Ruby. La primera es abrir el interpretador de Ruby ejecutando el comando IRB.

```
$ irb
2.3.0 :001 >
```

El interpretador nos permite escribir cualquier expresión válida de Ruby y oprimir `Enter`. El interpretador evalúa la expresión y debajo muestra el resultado:

```
$ irb
2.3.0 :001 > 1 + 2
  => 3
2.3.0 :002 >
```

Puedes repetir ese mismo proceso las veces que quieras. Esa es una forma muy rápida de probar código. Para salir escribe `exit` y oprime `Enter`.

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

Veamos ahora qué pasa si cometemos algún error en nuestro código. Por ejemplo, borra el caracter `u` de la palabra `puts`:

```
pts "Hola Mundo"
```

Vuelve a ejecutar el archivo con `ruby hello_world.rb`. Te debería aparecer el siguiente mensaje de error:

```
$ ruby hello_world.rb
hello_world.rb:1:in `<main>`: undefined method `pts` for main:Object (NoMethodError)
Did you mean? puts
```

El mensaje nos dice que el error ocurrió en el archivo `hello_world.rb` en la línea `1`, y que no se encuentra el método `pts`. Además nos da una sugerencia (correcta en este caso) preguntándonos si nos estábamos refiriendo al método `puts`.

Hay veces que es fácil encontrar los errores, otras veces no es tan fácil. Lo que si es cierto es que a medida que vayas trabajando con el lenguaje vas a ir desarrollando una intuición que te va a permitir solucionar los errores más fácilmente, pero al principio es un proceso lento que es parte de ese aprendizaje.

Cometamos otro error intencionalmente para ver un mensaje diferente. Vuelve a escribir `puts` correctamente, pero ahora borra la comilla al final de esa línea:

```
puts "Hola Mundo
```

Vuelve a ejecutar el archivo. Debería salir un mensaje como el siguiente:

```
$ ruby hello_world.rb
hello_world.rb:1: unterminated string meets end of file
```

Esta vez nos dice que hay una cadena de texto que no está terminada y se encuentra con el final del archivo, o se alarga hasta el final del archivo.

## Escribiendo más líneas

Vuelve a agregar la comilla y verifica que se ejecute normalmente.

Ruby ejecuta el archivo línea por línea, una después de la otra. Así que podemos agregar una segunda línea a nuestro archivo:

```ruby
puts "Hola mundo"
puts "Esto está muy bacano"
```

El comando `puts` se utiliza para imprimir una cadena de texto en la consola y al final de cada cadena de texto agrega un salto de línea (un `Enter`). Si no quieres que agregue ese salto de línea al final utiliza `print` en vez de `puts`.

```ruby
print "Hola mundo"
print "Esto está muy bacano"
```

Si lo ejecutamos

```
$ ruby hello_world.rb
Hola mundoEsto está muy bacano
```

Aparecen las dos cadenas en una misma línea. El print lo vamos a usar más adelante. Por ahora vuelve a cambiarlo por `puts`.

## Comentarios

Los comentarios se utilizan para documentar o aclarar nuestro código. Para agregar un comentario se utiliza el caracter `#`:

```ruby
# este es un comentario
puts "Hola mundo"
puts "Esto está muy bacano" # este es otro comentario
```

En este caso hemos agregado dos comentarios: el de la primera línea y el que está al final del último `puts`. Los comentarios son ignorados por Ruby así que deberías ver el mismo resultado que antes cuando ejecutes el archivo.

Agreguemos un nuevo comentario:

```ruby
# este es un comentario
# puts "Hola mundo"
puts "Hola mundo"
puts "Esto está muy bacano"
```

Fíjate que en el nuevo comentario estamos escribiendo código Ruby válido, pero por estar en un comentario Ruby lo ignora completamente.


## Evalúate

Escribas las respuestas a las siguientes preguntas (en papel o digitalmente) para que afiances los conceptos.

1. ¿Qué es IRB?

2. ¿Qué extensión tienen los archivos de Ruby?

3. ¿Cómo imprimimos "Me gusta Ruby!" desde un archivo de texto?

4. ¿Cómo se ejecuta un archivo de Ruby?

5. ¿Qué caracter se utiliza para agregar comentarios en Ruby?
