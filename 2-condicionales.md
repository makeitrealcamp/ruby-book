# Condicionales

Hasta ahora hemos visto código que se ejecuta línea a línea, una detrás de otra. Pero a veces se hace necesario romper esa secuencia y crear ramas que nos permitan tomar diferentes caminos en el código dependiendo de ciertas condiciones.

Por ejemplo, imagina cómo podríamos hacer un programa que nos diga si un número es mayor o menor a diez. Si es mayor a 10 debería imprimir una cosa, pero si es menor debería imprimir otra.

A este concepto se le conoce como condicionales y su sintaxis es la siguiente:

```ruby
if <condición>
  # código que se ejecuta si se cumple la condición
end
```

Empieza creando un archivo llamado `conditionals.rb` con el siguiente contenido:

```ruby
if true
  puts "Hola mundo"
end
```

Ejecútalo varias veces. En todas debería imprimir "Hola mundo":

```shell
$ ruby conditionals.rb
Hola mundo
```

Ahora probemos con falso.

```ruby
if false
  puts "Hola mundo"
end
```

Ejecútalo. Esta vez **nunca** debería imprimir "Hola mundo", no importa cuantas veces lo ejecutes.

También podemos utilizar algo que evalúe a verdadero o falso en la condición. Por ejemplo:

```ruby
if 1 == 1
  puts "Hola mundo"
end
```

El resultado al ejecutarlo debería ser:

```shell
$ ruby conditionals.rb
Hola mundo
```

Prueba ahora con `1 == 2`, `1 < 6` y `8 < 6` en la condición y fíjate que tenga sentido.

Ahora que ya sabes cómo funciona los condicionales (muchos los llamamos los ifs) crea un programa en un archivo llamado `number.rb` que le pida al usuario que ingrese un número e imprima "El número es menor a 10" solo si el número que ingresó el usuario es menor a 10:

```ruby
print "Ingresa un número: "
num = gets.chomp.to_i
if num < 10
  puts "El número es menor a 10"
end
```

Si lo ejecutas e ingresas un número menor a 10 te debería salir lo siguiente:

```shell
$ ruby number.rb
Ingresa un número: 5
El número es menor a 10
```

Ahora modifica el programa para que imprima "El número es igual o mayor a 10" si el número que ingresó el usuario es igual o mayor a 10:

```ruby
print "Ingresa un número: "
num = gets.chomp.to_1
if num < 10
  puts "El número es menor a 10"
end

if num >= 10
  puts "El número es igual o mayor a 10"
end
```

Prueba el programa con un número menor a 10, otro igual a 10 y otro mayor a 10.

Realmente todo lo que necesitamos para hacer condicionales es el `if ... end`. Con el `if ... end` podemos hacer cualquier tipo de condicional. Pero existen dos atajos que se utilizan para escribir código más corto. El primero es el `else`, que significa "de lo contrario", y nos permite ejecutar algún código cuando no entra al `if`.  Podemos reescribir el código anterior de la siguiente forma:

```ruby
print "Ingresa un número: "
num = gets.chomp.to_1
if num < 10
  puts "El número es menor a 10"
else
  puts "El número es igual o mayor a 10"
end
```

Más corto y debería funciona igual. Ahora supongamos que queremos modificar este programa para que imprima cuando el número es menor a 10, cuando el número es mayor a 10, y cuando el número es igual a 10. ¿Cómo te imaginas que podemos hacerlo?

Una solución es anidar los ifs de la siguiente forma:

```ruby
print "Ingresa un número: "
num = gets.chomp.to_1
if num < 10
  puts "El número es menor a 10"
else
  # acá solo entra si el número es igual o mayor a 10
  if num > 10
    puts "El número es mayor a 10"
  else
    puts "El número es igual a 10"
  end
end
```

Otra mejor solución es utilizar otro atajo que nos ofrece Ruby, el `elsif`:

```ruby
print "Ingresa un número: "
num = gets.chomp.to_1
if num < 10
  puts "El número es menor a 10"
elsif num > 10
  puts "El número es mayor a 10"
else
  puts "El número es igual a 10"
end
```

Lo más importante de entender de este código es que el programa solo va a entrar a **una** de estas ramas. Por ningún motivo va a entrar a dos. Ruby primero evalúa la condición del `if`, y si es true, ejecuta el código y salta hasta después del `end` sin evaluar las siguientes condiciones. En cambio, si evalúa a false, sigue con la evaluación del `elsif`, y si es `true`, ejecuta el código dentro de ese `elsif` y salta hasta después del `end`.

Bien, ahora supongamos que queremos escribir un programa que le pida al usuario un número e imprima "El número está entre 10 y 20" si el número que ingrese el usuario está efectivamente entre 10 y 20. ¿Cómo te imaginas que lo podríamos solucionar?

Una opción es usar ifs anidados, entonces:

```ruby
num = 15
if num >= 10
  if num <= 20
    puts "El número está entre 10 y 20"
  end
end
```

El problema es que si ahora queremos imprimir "El número no está entre 10 o 20" cuando el número que ingrese el usuario no esté entre 10 y 20, se nos va a dificultar. 

Por ejemplo, supongamos que el número es 25. 25 es mayor a 10 así que va a entrar al primer `if`. Sin embargo, 20 **no** es menor que 20, así que no va a entrar al segundo `if`. Una solución sería repetir algo de código:

```ruby
num = 15
if num >= 10
  if num <= 20
    puts "El número está entre 10 y 20"
  else
    puts "El número no está entre 10 y 20"
  end
else
  puts "El número no está entre 10 y 20"
end
```

Pero este código es difícil de entender. En general uno debe tratar de evitar los `ifs` anidados porque son difíciles de entender. Afortunadamente Ruby nos da las herramientas para solucionar este problema (al igual que la mayoría de lenguajes) y es utilizar `y` y `o` en las condiciones. En este caso podemos arreglar el código anterior de la siguiente forma:

```ruby
num = 15
if num >= 10 && num <= 20
  puts "El número está entre 10 y 20"
end
```

El `y` se representa con `&&`. Fíjate que en cada lado del `&&` hay una expresión que evalúa a verdadero o falso. 

También existe el `o`. Supongamos que queremos escribir un programa que le pida un color al usuario y diga excelente elección solo si el color es rojo **o** negro. Una solución que no requiere el `o` es la siguiente:

```ruby
color = gets.chomp
if color == "negro"
  puts "Excelente elección"
end

if color == "blanco"
  puts "Excelente elección"
end
```

Sin embargo, acá nos estamos repitiendo, así que lo podemos mejorar con un `o`:

```ruby
color = gets.chomp
if color == "negro" || color == "blanco"
  puts "Excelente elección"
end
```

Mucho mejor. Pero este es el punto en que se puede complicar. Supongamos ahora que le queremos pedir un número y un color al usuario, y queremos imprimir "Excelente elección" si el color es negro y el número está entre 10 y 20, o si el color es diferente a verde y el número es menor a 10. Podemos combinar `&&` y `||` en una expresión más compleja:

```ruby
num = gets.chomp.to_i
color = gets.chomp
if (color == "negro" && (num >= 10 && num <= 20)) || (color != "verde" && num < 10)
  puts "Excelente elección"
end
```

En general es mejor evitar condicionales tan complejas. Pero si te encuentras con algo así, lo mejor es reemplazar las variables con algunos valores y empezar a simplificar la expresión de la siguiente forma:

```
num = 15
color = "verde"
(false && (true && true)) || (false && false) # reemplazamos las variables y quedamos con esta expresión
(false && (    true    )) || (     false    ) # simplificamos un nivel más
         false            ||       false      # simplificamos lo de la izquierda
                        false                 # false || false es false
```

Para este tipo de problemas se han desarrollado las tablas de verdad. Veamos la tabla de verdad del `&&` y del `||`, que son las más comunes. La tabla del `&&` es la siguiente:

| Expresión | Resultado | 
| --- | --- |
| `true && true` | `true` | 
| `true && false` | `false` |
| `false && true` | `false` |
| `false && false` | `false` |

La tabla del `||` es la siguiente:

| Expresión | Resultado | 
| --- | --- |
| `true || true` | `true` | 
| `true || false` | `true` |
| `false || true` | `true` |
| `false || false` | `false` |

Con mi hija practico un juego en donde le digo frases como: "Prende la luz si tu mamá está en la sala **y** hoy es viernes". Ella tiene que decidir si prende la luz o no. En este caso solo debe prender la luz si las dos condiciones se cumplen (que su mamá esté en la sala y hoy sea viernes). 

En cambio, si le digo "Prende la luz si tu mamá está en la sala **o** hoy es viernes", ella debe prender la luz si cualquier condición se cumple. Por debajo debe aplicar las tablas de verdad pero es mucho más intuitivo aprenderlo así.

Bien, por último vamos a ver la negación. Supongamos que queremos escribir un programa que le pregunta al usuario si está lloviendo o no, y si está lloviendo, diga algo como "No, no puedes salir".

Como siempre, en programación hay muchas formas de llegar a la misma solución. Y tu primera tarea es que funcione, no importa cómo. Se me ocurren las siguientes soluciones a este problema:

```ruby
print "¿Está lloviendo? (S o N): "
input = gets.chomp
not_raining = input == "N"

if not_raining
  puts "No, no puedes salir"
end
```

Primero le pedimos al usuario que ingrese `S` o `N` si está lloviendo o no. Después comparamos si lo que ingresa el usuario es `N` (no está lloviendo) y lo almacenamos en la variable `not_raining`. Por último, el `if` solo entra si la variable `not_raining` es `true`.

Otra solución sería:

```ruby
print "¿Está lloviendo? (S o N): "
input = gets.chomp
raining = input == "S"

if raining

else
  puts "No, no puedes salir"
end
```

Pero no es muy recomendable dejar ifs vacíos. La mejor opción sería:

```ruby
print "¿Está lloviendo? (S o N): "
input = gets.chomp
raining = input == "S"

if !raining
  puts "No, no puedes salir"
end
```

Es similar a la primera, pero en vez de crear una variable `not_raining` mejor creamos una que sea `raining` que va a tener el valor de `true` si está lloviendo, `false` de lo contrario. Y en la condición del `if` utilizamos `!raning` (`!` es negación), que significa si no está lloviendo (si `raining` es `true` la condición evalúa a `false`, pero si `raining` es `false` la condición evalúa a `true`).

Hagamos un programa que nos diga de qué generación somos dependiendo de nuestro año de nacimiento. Las generaciones son las siguientes:

```
Nacidos <= 1945 - la gran generación
Nacidos entre 1946 y 1964 - baby boomers
Nacidos entre 1965 y 1982 - generación x
Nacidos entre 1983 y 2004 - milenials
Nacidos >= 2005 - centenials
```

Bien, crea un archivo `generation.rb` y escribe lo siguiente:

```ruby
print "¿Cuál es tu año de nacimiento? "
year_of_birth = gets.chomp.to_i

if year_of_birth >= 2005
  puts "Eres un centenial"
elsif year_of_birth >= 1983
  puts "Eres un millenial"
elsif year_of_birth >= 1965
  puts "Eres generación X"
elsif year_of_birth >= 1946
  puts "Eres baby boomer"
else
  puts "Eres tradicionalista"
end
```

Intenta entenderlo. ¿Por qué en los `elsif` solo estamos comparando si el año es mayor o igual? ¿Por qué no es necesario comparar que el año se menor que el de la siguiente generación como en el siguiente código?

```ruby
print "¿Cuál es tu año de nacimiento? "
year_of_birth = gets.chomp.to_i

if year_of_birth >= 2005
  puts "Eres un centenial"
elsif year_of_birth >= 1983 && year_of_birth < 2005
  puts "Eres un millenial"
elsif year_of_birth >= 1965 && year_of_birth < 1983
  puts "Eres generación X"
elsif year_of_birth >= 1946 && year_of_birth < 1965
  puts "Eres baby boomer"
else
  puts "Eres tradicionalista"
end
```
