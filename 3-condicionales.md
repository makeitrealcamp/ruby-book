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

Ejecútalo varias veces. En todas debería imprimir `"Hola mundo"`:

```
$ ruby conditionals.rb
Hola mundo
```

Ahora probemos con falso.

```ruby
if false
  puts "Hola mundo"
end
```

Ejecútalo. Esta vez **nunca** debería imprimir `"Hola mundo"`, no importa cuantas veces lo ejecutes.

También podemos utilizar algo que evalúe a verdadero o falso en la condición. Por ejemplo:

```ruby
if 1 == 1
  puts "Hola mundo"
end
```

El resultado al ejecutarlo debería ser:

```
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

```
$ ruby number.rb
Ingresa un número: 5
El número es menor a 10
```

Ahora modifica el programa para que imprima "El número es igual o mayor a 10" si el número que ingresó el usuario es igual o mayor a 10:

```ruby
print "Ingresa un número: "
num = gets.chomp.to_i

if num < 10
  puts "El número es menor a 10"
end

if num >= 10
  puts "El número es igual o mayor a 10"
end
```

Ejecuta el programa e ingresa un número menor a 10, después un número mayor a 10, y por último 10. Verifica que el resultado sea el esperado.

## De lo contrario (else)

Lo único que necesitas para hacer condicionales es el `if`. Pero existen dos atajos que te van a permitir escribir código más corto.

El primer atajo es el `else`, que significa "de lo contrario" en Inglés. El `else` nos permite definir el código que se debe ejecutar si el `if` no se cumple, es decir si la condición evalúa a falso. La sintaxis es la siguiente:

```ruby
if <condicion>
  # código que se ejecuta si se cumple la condición
else
  # código que se ejecuta si NO se cumple la condición
end
```

Podemos modificar el programa anterior, que nos dice si el número almacenado en la variable `num` es menor a 10, o si es mayor o igual, con un `else`.

```ruby
print "Ingresa un número: "
num = gets.chomp.to_i

if num < 10
  puts "El número es menor a 10"
else
  puts "El número es igual o mayor a 10"
end
```

Más corto y si lo ejecutas debería funcionar igual.

## Condiciones anidadas

Ahora imagina que queremos modificar este programa para que imprima:

* `"El número es menor a 10"` si el número es **menor** a 10.
* `"El número es mayor a 10"` si el número es **mayor** a 10.
* `"El número es igual a 10"` si el número es **igual** a 10.

En Ruby (y en la mayoría de lenguajes de programación) es posible anidar condicionales, así que una posible solución sería la siguiente:

```ruby
print "Ingresa un número: "
num = gets.chomp.to_i

if num < 10
  puts "El número es menor a 10"
else
  if num > 10
    puts "El número es mayor a 10"
  else
    puts "El número es igual a 10"
  end
end
```

Prúebalo con un número menor a 10, otro mayor a 10 y con 10. Te debería mostrar `"El número es menor a 10"`, `"El número es mayor a 10"` y `"El número es igual a 10"` respectivamente.

## De lo contrario, si (else if)

En general, es preferible no tener que anidar condicionales porque son difíciles de leer y entender. Otro atajo que nos ofrece Ruby para los condicionales es el `elsif`, que significa "de lo contrario, si" en Inglés. La sintaxis es la siguiente:


```ruby
if <condicion_1>
  # código que se ejecuta si se cumple la condición_1
elsif <condicion_2>
  # código si <condicion_1> NO se cumple, pero <condicion_2> sí
elsif <condicion_3>
  # código si <condicion_1> y <condicion_2> NO se cumplen, pero <condicion_3> sí
else
  # código si ninguna de las condiciones se cumple
end
```

Puedes definir tantos `elsif` como desees. El `else` es opcional.

Modifiquemos nuestro ejemplo anterior y en vez de utilizar condiciones anidadas, utilicemos `else if`:

```ruby
print "Ingresa un número: "
num = gets.chomp.to_i

if num < 10
  puts "El número es menor a 10"
elsif num > 10
  puts "El número es mayor a 10"
else
  puts "El número es igual a 10"
end
```

Lo más importante de entender en este código es que el programa sólo va a entrar a **una** de estas ramas. Por ningún motivo va a entrar a dos de ellas. Si la condición del primer `if` se cumple, el programa ejecuta el código que esté en ese bloque y después **salta** hasta después del `else` para continuar con el resto del programa o terminar.

Si la condición del primer `if` no se cumple, pero la del `elsif` sí se cumple, el programa ejecuta el código de ese bloque y **salta** hasta después del `else` para continuar con el resto del programa o terminar.

## Condiciones compuestas

Imagina que queremos escribir un programa que imprima "El número está entre 10 y 20" si el valor de una variable está efectivamente entre 10 y 20. ¿Cómo te imaginas que lo podríamos solucionar?

Una opción es usar condiciones anidadas, de esta forma:

```ruby
num = 15
if num >= 10
  if num <= 20
    puts "El número está entre 10 y 20"
  end
end
```

Sin embargo, cómo decíamos antes, leer condiciones anidadas es difícil y, en lo posible, es mejor evitarlas. En cambio, podemos utilizar los operadores lógicos **y** (`&&`) y **ó** (`||`) para crear condiciones compuestas. El ejemplo anterior lo podemos mejorar con **y**:

```ruby
num = 15
if num >= 10 && num <= 20
  puts "El número está entre 10 y 20"
end
```

La `y` se representa con `&&`. Lo que estamos diciendo con este código es: si el número es **mayor o igual a 10 y menor o igual 20** entonces imprima "El número está entre 10 y 20". Fíjate que a cada lado del `&&` hay una expresión que evalúa a verdadero o falso: `num >= 10` y `num <= 20`.

También existe el **o**, que se representa con `||`. Imagina ahora que necesitamos escribir un programa que imprima "Excelente elección" cuando el valor de una variable sea "rojo" **o** "negro":

```ruby
color = gets.chomp
if color == "negro" || color == "blanco"
  puts "Excelente elección"
end
```

## Pensando como un programador

Vamos a jugar un juego llamado **Verdadero o Falso**. Yo digo una afirmación y tu debes reponder "verdadera" si la afirmación es verdadera o "falsa" si es falsa. Trata de no mirar las respuestas debajo. Después comparas:

1. La Tierra gira alrededor del sol.
2. Paris es la capital de Estados Unidos.
3. La Tierra gira alrededor del sol **y** los leones son animales.
4. Paris es la capital de Estados Unidos **y** los leones son animales.
5. La Tierra gira alrededor de Marte **y** los perros hablan Español.
6. Los leones son animales **o** la Tierra gira alrededor del sol.
7. Paris es la capital de Estados Unidos **o** los leones son animales.
8. El planeta tierra gira alrededor de Marte **o** los perros hablan Español.

Las respuestas son las siguientes:

1. Verdadera.
2. Falsa.
3. Verdadera.
4. Falsa.
5. Falsa.
6. Verdadera.
7. Verdadera.
8. Falsa.

Fíjate que cuando utilizamos **y** las dos afirmaciones deben ser verdaderas para que el resultado sea verdadero. Cuando utilizamos **o** cualquiera de las dos afirmaciones puede ser verdadera para que el resultado sea verdadero.

### Evaluando expresiones booleanas

Volvamos a jugar el juego, pero en vez de utilizar afirmaciones, utilicemos expresiones booleanas. Debes decidir si cada una de las siguientes expresiones es verdadera o falsa (`true` o `false`):

1. `true`
2. `false`
3. `1 < 1`
4. `2 != 3`
5. `1 < 1 && 2 != 3`

Copia y pega cada expresión en IRB para conocer las respuestas.

Analicemos la última expresión: `1 < 1 && 2 != 3`. ¿Cómo podemos saber si es verdadera o falsa?

El primer paso es reemplazar cada lado de la expresión. `1 < 1` es `false` y `2 != 3` es `true`. Quedaría:

`false && true`

Recuerda que para que una expresión con **y** (`&&`) sea verdadera, cada lado **tiene** que ser verdadero. Sin embargo, podemos hacer una tabla con todas las combinaciones entre verdadero y falso para poder usarla como referencia más adelante:

| Expresión | Resultado |
| --- | --- |
| `true && true` | `true` |
| `true && false` | `false` |
| `false && true` | `false` |
| `false && false` | `false` |

Fíjate que para que el resultado sea `true` los dos lados del `&&` **deben ser** `true`.

Hagamos lo mismo para el **o** (`||`):

| Expresión | Resultado |
| --- | --- |
| <code>true &#124;&#124; true</code> | `true` |
| <code>true &#124;&#124; false</code> | `true` |
| <code>false &#124;&#124; true</code> | `true` |
| <code>false &#124;&#124; false</code> | `false` |

Con el **ó** cualquiera de los lados puede ser `true` para que el resultado sea `true`.

A estas tablas se les conoce como **Tablas de Verdad**.

Hagamos algunos ejercicios. Decide si las siguientes expresiones evalúan a `true` o `false`. Primero reemplaza cada lado del `&&` o el `||` y luego utiliza las tablas de verdad:

* `"hola" == "hola" && 1 < 2`
* `true && 5 != 5`
* `1 == 1 || 2 != 1`

Revisa tu respuesta evaluando cada expresión en IRB.

Podemos negar cualquier expresión booleana anteponiendo un signo de exclamación (`!`). Por ejemplo:

* `!true` es `false`
* `!false` es `true`

De hecho, esa es la tabla de verdad de la negación. Intenta los siguientes ejercicios. Primero reemplaza lo que está entre paréntesis y luego aplica la tabla de verdad de la negación:

* `!(1 === 1)`
* `!(2 <= 3)`
* `!(true && 5 !== 5)`
* `!(1 < 1 && 2 !== 3)`

El proceso para solucionar cualquier expresión booleana, sin importar qué tan compleja sea, es el siguiente:

1. Evalúa los operadores de igualdad (`<`, `>`, `===`, `!==` etc).
2. Evalúa los `&&` y `||` que esten dentro de paréntesis.
3. Evalúa las negaciones (`!`).
4. Evalúa cualquier `&&` y `||` que falte.

Hagamoslo juntos. Intentemos evaluar la siguiente expresión booleana:

```
3 != 4 && !("pedro" === "juan" || 26 > 10)
```

1. Evaluar los operadores de igualdad:

   ```
   true && !(false || true)
   ```

2. Evaluar los `&&` y `||` que estén dentro de paréntesis:

   ```
   true && !true
   ```

3. Evaluar las negaciones:

   ```
   true && false
   ```

4. Evaluar cualquier `&&` y `||` que falte:

   ```
   false
   ```

Inténtalo tu. Decide si las siguientes expresiones evalúan a `true` o `false`:

* `!(5 === 5) && 8 !== 8`
* `("gut" === "ikk" && 26 > 30) || ("gut" === "gut" && 26 > 10)`
* `!("testing" == "testing" && !(5 > 8))`

## Evalúate

1. ¿Cuál es la syntaxis de un `if` (sin `else` o `elsif`)?

2. ¿En qué caso se ejecuta el código que está dentro del `if`?

3. ¿En qué caso se ejecuta el código que está dentro del `else`?

4. ¿Cuántos `else` pueden existir en un condicional?

5. ¿Cuántos `elsif` pueden existir en un condicional?

6. ¿Qué problema tiene el siguiente código?

   ```rb
   if num >= 10 && <= 20
     puts "El número está entre 10 y 20"
   end
   ```

7. ¿Cuál es el resultado de evaluar `!(1 == 1)`?

8. ¿Cuál es el resultado de evaluar `3 != 4 && !("pedro" === "juan" || 26 > 10)`?

9. ¿Qué imprimiría el siguiente código?

   ```rb
   raza = "Persa"
   ojos = "verdes"
   edad = 3

   if ojos == "rojos" || (edad > 2 && edad < 5)
     puts "Me lo llevo!"
   else
     puts "Paso!"
   end
   ```
