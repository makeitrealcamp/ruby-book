# Tipos y Operadores

En este capítulo vamos a hablar sobre cadenas de texto, números y booleanos (verdadero o falso), que son algunos de los tipos de datos en Ruby, y cómo realizar operaciones básicas con ellos.

## Cadenas de texto

Una cadena de texto es un conjunto de caracteres encerrados entre comillas simples (`'`) o dobles (`"`). Por ejemplo:

```rb
"Texto entre comillas dobles"
'Texto entre comillas simples'
```

Aunque parece fácil, existen tres errores comunes que cometen los principiantes al definir una cadena de texto para que los tengas en cuenta e intentes evitarlos:

1. Olvidarse de la comilla de cierre. Por ejemplo:

   ```
   "Hola mundo
   ```
2. Cerrar la cadena con la comilla incorrecta (p.e. abrir la cadena con comilla doble y cerrarla con comilla sencilla). Por ejemplo:

   ```
   "Hola mundo'
   ```
3. Insertar el mismo tipo de comillas que se usó para definir la cadena dentro del texto. Por ejemplo:

   ```
   "Y con las palabras "Hola Mundo" creó Ruby"
   'Vamos pa' lante'
   ```

Si necesitas insertar una comilla en el texto, utiliza un tipo de comilla diferente para definir la cadena. Por ejemplo, los ejemplos del último punto los podemos solucionar de la siguiente forma.

```rb
'Y con las palabras "Hola Mundo" creó Ruby'
"Vamos pa' lante"
```

**Recuerda:** Lo importante es que el texto no contenga la comilla que se utilizó para definir la cadena.

Pero ¿qué pasa si tenemos un texto con comillas simples y dobles? En ese caso tendríamos que utilizar el caracter de escape `\` como en el siguiente ejemplo:

```rb
'Y con las palabras "vamos pa\' lante" creó Ruby'
```

O

```rb
"Y con las palabras \"vamos pa' lante\" creó Ruby"
```

En el primer ejemplo escapamos con `\` la comilla simple porque con esas fue que encerramos el texto, mientras que en el segundo ejemplo escapamos las comillas dobles porque con esas fue que encerramos el texto.

## Números

Crea un nuevo archivo llamado `numbers.rb` y transcribe el siguiente código:

```rb
puts 1 + 2
puts 3 * 4 + 5
puts 8 / 2
```

Si lo ejecutas deberías ver algo así:

```
$ ruby numbers.rb
3
17
4
```

Fíjate en la segunda línea del ejemplo. Ruby sigue el mismo estandar que en matemáticas, y por lo tanto la multiplicación se ejecuta primero que la suma. Puedes cambiar el comportamiento con paréntesis. Por ejemplo, cambia la operación de la segunda línea por `3 * (4 + 5)`. El resultado ahora debería ser `27`.

A diferencia de las cadenas de texto, los números no se encierran entre comillas de ninún tipo (de lo contrario Ruby los trata como texto y no como números). Por ejemplo, abre IRB y escribe `"1" + "2"`. El resultado ya no es `3`, es la cadena de texto `"12"`:

```
$ irb
> "1" + "2"
'12'
```

## Valores y expresiones booleanas

Existen dos valores booleanos en programación: verdadero (`true`) y falso (`false`). Abre IRB, escribe `true` y oprime Enter, después escribe `false` y oprime Enter. El resultado debe ser el siguiente:

```
$ irb
> true
true
> false
false
```

También es posible escribir **expresiones** que evalúen a `true` o `false`. Escribe ahora las siguientes expresiones en IRB:

* `5 > 3`
* `5 >= 3`
* `4 < 4`
* `4 <= 4`
* `2 == 2`
* `2 != 2`

El resultado debería ser el siguiente:

```
$ irb
> 5 > 3
 => true
> 5 >= 3
 => true
> 4 < 4
 => false
> 4 <= 4
 => true
> 2 == 2
 => true
> 2 != 2
 => false
> "ruby" == "javascript"
 => false
> "ruby" != "javascript"
 => true
```

A los operadores `<`, `>`, `<=`, `>=`, `==`, `!=` se les llama **operadores lógicos** y se utilizan para crear expresiones que se evalúan a un valor booleano: verdadero (`true`) o falso (`false`).


## Imprimiendo en la línea de comandos

Para imprimir un valor en la línea de comandos utilizamos la palabra `puts` como hicimos en el capítulo anterior:

```rb
puts "Y con las palabras \"vamos pa' lante\" creó Ruby"
```

Si guardas esa línea en un archivo llamado `strings.rb` y lo ejecutas, el resultado debería ser el siguiente:

```
$ ruby strings.rb
Y con las palabras "vamos pa' lante" creó Ruby
```

## Concatenando cadenas

Es posible unir cadenas de texto con el operador `+`. Por ejemplo, abre IRB y ejecuta lo siguiente:

```rb
"Hola" + "Mundo" + "Cómo" + "Estás"
```

Deberías ver algo como esto:

```
$ irb
> "Hola" + "Mundo" + "Cómo" + "Estás"
 => "HolaMundoCómoEstás"
```

Fíjate que las palabras no se separan con espacio automáticamente, tenemos que agregar los espacios explícitamente:

```
$ irb
> "Hola " + "Mundo " + "Cómo " + "Estás"
 => "Hola Mundo Cómo Estás"
```

### Concatenando valores de diferentes tipos

Si intentas concatenar una cadena con un número vas a ver el siguiente error:

```
$ irb
> "Hola" + 3
TypeError: no implicit conversion of Fixnum into String
	from (irb):1:in `+'
	from (irb):1
	from /Users/germanescobar/.rvm/rubies/ruby-2.3.0/bin/irb:11:in `<main>'
```

El error nos dice que no es posible convertir un `Fixnum` (un número) a un `String` (a una cadena de texto). Una solución a este problema es convertir explícitamente el número a una cadena añadiendo `.to_s` a la derecha del número:

```
$ irb
> "Hola" + 3.to_s
 => "Hola3"
```

Ahora intenta lo siguiente, queremos que imprima `"2 + 3 es 5"`:

```
$ irb
> "2 + 3 es " + 2 + 3
TypeError: no implicit conversion of Fixnum into String
	from (irb):6:in `+'
	from (irb):6
	from /Users/germanescobar/.rvm/rubies/ruby-2.3.0/bin/irb:11:in `<main>'
```

¿Qué pasa si le añadimos `.to_s` a cada número? Veamos:

```
$ irb
> "2 + 3 es " + 2.to_s + 3.to_s
 => "2 + 3 es 23"
```

No es el resultado que esperábamos. Lo que hizo Ruby fue concatenar la cadena `"2 + 3 es "` con las cadenas `"2"` y `"3"`.

Una solución es envolver la suma entre paréntesis y agregarle `.to_s`:

```
$ irb
> "2 + 3 es " + (2 + 3).to_s
 => "2 + 3 es 5"
```

Pero estar convirtiendo los tipos a cadena de texto con `.to_s` es muy engorroso. Ruby nos ofrece una mejor solución, la interpolación:

## Interpolación

La interpolación es la forma recomendada de concatenar cadenas en Ruby. Abre IRB e intenta lo siguiente:

```
$ irb
> "Hola #{4}"
 => "Hola 4"
```

La interpolación nos permite ejecutar código Ruby dentro de una cadena de texto, convertir el resultado a una cadena de texto y reemplazarlo en donde se definió. Por ejemplo:

```
$ irb
> "2 + 3 es #{2 + 3}"
 => "2 + 3 es 5"
```

Para usar interpolación ten en cuenta lo siguiente:

* Debes usar comillas dobles (`"`) en vez de sencillas (`'`). Si utilizas comillas sencillas Ruby ignora la interpolación:

  ```
  $ irb
  > '2 + 3 es #{2 + 3}'
   => "2 + 3 es #{2 + 3}"
  ```

* La sintaxis de la interpolación es `#{}`. Ruby evalúa lo que esté entre los corchetes y lo convierte en cadena de texto.
* Puedes usar `#{}` las veces que quieras dentro de una cadena.

## Evalúate

1. ¿Cuál es el problema con la siguiente cadena de texto y de qué formas lo podríamos solucionar?

   ```
   "Palabras: "Agua", "Tierra""
   ```

2. ¿Cuál sería el resultado de la siguiente expresión?

   ```
   3 + "3"
   ```

3. ¿Qué problema tiene el siguiente código y cómo lo podemos solucionar para que evalúe a `true`?

   ```
   3 = 3
   ```

4. ¿Qué es la interpolación y para qué se utiliza?
