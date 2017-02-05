# Iteraciones o ciclos

Los ciclos nos permiten repetir la ejecución de un código varias veces. Imagina que quisiéramos repetir la frase "Hola mundo" 5 veces. Podríamos hacerlo manualmente. Crea un archivo llamado `loops.rb` y escribe el siguiente código:

```ruby
puts "Hola mundo"
puts "Hola mundo"
puts "Hola mundo"
puts "Hola mundo"
puts "Hola mundo"
```

Ejecútalo y deberías ver la frase "Hola mundo" 5 veces en tu pantalla:

```
$ ruby loops.rb
Hola mundo
Hola mundo
Hola mundo
Hola mundo
Hola mundo
```

Ahora imagina que quisieramos repetirlo 850 veces. Ya no sería tan divertido copiar todo ese número de líneas en el archivo. Podemos entonces utilizar un ciclo. Un ciclo se crea utilizando la palabra clave `while` seguido de una condición que va a definir el número de veces que se va a repetir ese ciclo. Reemplaza el contenido del archivo `loops.rb` por el siguiente:

```ruby
i = 0
while i < 850
  puts "Hola mundo"
  i = i + 1
end
```

Ejecútalo y revisa que la frase "Hola mundo" aparezca 850 veces. Como ejercicio modifícalo para que aparezca el valor de `i` antes de cada frase. Debería salir algo así (omitimos algunas líneas para no gastar tanto pap...ehhh...espacio en disco):

```
$ ruby loops.rb
0 Hola mundo
1 Hola mundo
2 Hola mundo
...
345 Hola mundo
...
849 Hola mundo
```

Un ciclo tiene la siguiente sintaxis:

```ruby
while <condición>
  # acá va el código que se va a repetir mientras la condición sea verdadera
end
```

El código que está entre el `while` y el `end` se va a repetir mientras que la condición sea verdadera. Crea un archivo llamado `infinite_loop.rb` que contenga lo siguiente:

```ruby
while true
  puts "Hola mundo"
end
```

¿Qué crees que va a ocurrir? Antes de ejecutarlo debes saber que puedes interrumpir cualquier programa oprimiendo `Ctrl + C` :)

El código anterior crea lo que en programación llamamos un **ciclo infinito**. También podemos crear un ciclo que nunca va a ejecutar el código que contiene:

```ruby
while false
  puts "Hola mundo"
end
```

Si ejecutas ese código no deberías ver ninguna frase "Hola mundo".

En vez de `true` o `false` puedes utilizar cualquier otra condición como lo hicimos en el ciclo que muestra "Hola mundo" 850 veces:

```ruby
i = 0
while i < 850
  puts "Hola mundo"
  i = i + 1
end
```

Primero declaramos una variable `i` que inicia en 0. Cada vez que ingresa en el ciclo la vamos a incrementar en 1 hasta que lleguemos a 850. En ese momento la condición va a dejar de ser verdadero y el ciclo se detendrá.

Escribamos otro programa que le solicite al usuario un número, imprima "El número es menor a 10" y repita el proceso hasta que el usuario ingrese un número mayor o igual a 10. Crea un archivo llamado `input_loop.rb` y escribe lo siguiente.

```ruby
print "Ingresa un número: "
num = gets.chomp.to_i
while num < 10
  puts "El número es menor a 10"

  print "Ingresa un número: "
  num = gets.chomp.to_i
end
```

Si lo ejecutas debería preguntarte una y otra vez siempre y cuando el número sea menor a 10:

```
$ ruby input_loop.rb
Ingresa un número: 5
El número es menor a 10
Ingresa un número: 8
El número es menor a 10
Ingresa un número: 15
```

El `while ... end` es lo único que debes saber para hacer ciclos. Sin embargo, Ruby nos ofrece varias alternativas y atajos para escribir ciclos. Lo importante es que no olvides que cualquier cosa que puedes hacer con las alternativas también lo puedes hacer con el `while ... end`.

## Iterando N veces

Cuando simplemente queremos repetir un código N veces (como cuando queríamos mostrar 850 veces "Hola mundo") podemos utilizar el siguiente código:

```ruby
850.times do
  puts "Hola mundo"
end
```

Compáralo con el otro código. Mucho más corto y claro. El número no tiene que ser explícito, podría estar en una variable:

```ruby
num = 850
num.times do
  puts "Hola mundo"
end
```

Si necesitas la variable sobre la que estamos iterando (piensa en el `i` del otro código) puedes hacer lo siguiente:

```ruby
850.times do |i|
  puts "#{i} Hola mundo"
end
```

## Iterando sobre un rango

Supongamos que queremos iterar del número 10 al 15 (en un rango). Crea un archivo llamado `range_loop.rb` y escribe lo siguiente:

```ruby
(10..15).each do |i|
  puts "#{i} Hola mundo"
end
```

Al ejecutar este código deberías ver lo siguiente:

```
$ ruby range_loop.rb
10 Hola mundo
11 Hola mundo
12 Hola mundo
13 Hola mundo
14 Hola mundo
14 Hola mundo
```

Existen más formas de iterar en Ruby (Ruby es un lenguaje muy expresivo) pero estas son suficientes para que empieces a practicar.

## Evalúate

Intenta hacer un juego que genere un número aleatorio del 1 al 10 y le pida al usuario que lo adivine con intentos ilimitados (el programa acaba únicamente cuando lo ha adivinado). Al ejecutarlo debería funcionar de la siguiente forma:

```
$ ruby guess_num.rb
Adivina el número del 1 al 10 que estoy pensando: 5
¡No! Intenta nuevamente: 3
¡No! Intenta nuevamente: 6
¡No! Intenta nuevamente: 7
¡No! Intenta nuevamente: 4
Felicitaciones, lo adivinaste!
```

Si lo solucionas muy fácilmente modifícalo para limitar el número de intentos a 3.
