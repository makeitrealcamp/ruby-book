# Tipos y Operadores

En este capítulo vamos a hablar sobre cadenas de texto, números y booleanos (verdadero o falso), que son algunos tipos de datos en Ruby, y cómo realizar algunas operaciones básicas con ellos.

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
3. Insertar el mismo tipo de comillas dentro de la cadena de texto. Por ejemplo:

   ```
   "Y él dijo: "Hola Mundo""
   'Hol'a mundo'
   ```

Para solucionar el último error (punto 3) podemos encerrar la primera cadena entre comillas simples y la segunda entre comillas dobles para que funcione:

```rb
"Hol'a mundo"
'Y él dijo: "Hola mundo"'
```

**Recuerda:** Lo importante es que el texto no contenga la comilla que se utilizó para definir la cadena.

Pero ¿qué pasa si tenemos un texto con comillas simples y dobles? En ese caso tendríamos que utilizar el caracter de escape `\` como en el siguiente ejemplo:

```rb
'Y \'él dijo\': "Hola mundo"'
```

O

```rb
"Y 'él dijo': \"Hola mundo\""
```

En el primer ejemplo escapamos con `\` las comillas simples porque con esas fue que encerramos el texto, mientras que en el segundo ejemplo escapamos las comillas dobles porque con esas fue que encerramos el texto.

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

A diferencia de las cadenas de texto, los números no se encierran entre comillas de ninún tipo (de lo contrario Ruby los trata como texto y no como números). Por ejemplo, abre la consola de NodeJS y escribe `"1" + "2"`. El resultado ya no es `3`, es la cadena de texto `"12"`:

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

Para imprimir una cadena de texto en la línea de comandos (o en la consola del navegador) utilizamos la palabra `puts` como hicimos en el capítulo anterior:

```rb
puts 'Y \'él dijo\': "Hola mundo"'
```

Si guardas esa línea en un archivo llamado `strings.rb` y lo ejecutas, el resultado debería ser el siguiente:

```
$ ruby strings.rb
Y 'él dijo': "Hola mundo"
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

Si intentas concatenar una cadena con un número vas a recibir un error:

```
$ irb
> "Hola" + 3
TypeError: no implicit conversion of Fixnum into String
	from (irb):1:in `+'
	from (irb):1
	from /Users/germanescobar/.rvm/rubies/ruby-2.3.0/bin/irb:11:in `<main>'
```

El error nos dice que no es posible convertir un `Fixnum` (un número) a `String` (a una cadena de texto). Una solución a este problema es convertir explícitamente el número a una cadena añadiendo `.to_s` al número:

```
$ irb
> "Hola" + 3.to_s
 => "Hola3"
```

Pero ahora mira este ejemplo. Queremos que imprima `"2 + 3 es 5"`:

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

Una solución es envolver la suma en paréntesis y agregarle `.to_s`:

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

La interpolación nos permite ejecutar código Ruby dentro de una cadena de texto y convertir el resultado automáticamente a cadena de texto:

```
$ irb
> "2 + 3 es #{2 + 3}"
 => "2 + 3 es 5"
```

Para usar interpolación ten en cuenta lo siguiente:

* Debes usar comillas dobles (`"`), comillas sencillas (`'`) no funcionan. Inténtalo:

  ```
  $ irb
  > '2 + 3 es #{2 + 3}'
   => "2 + 3 es #{2 + 3}"
  ```

* La sintaxis de interpolación es `#{}`. Ruby evalúa lo que esté entre los corchetes y lo convierte en una cadena de texto.
* Puedes usar `#{}` las veces que quieras dentro de una cadena.

## Evalúate

1. ¿Cuál es el problema con la siguiente cadena de texto y de qué formas se podría solucionar?:

   ```
   "Palabras: "Agua", "Tierra""
   ```

2. ¿Cuál sería el resultado de la siguiente expresión?

   ```
   3 + "3"
   ```

3. ¿Cuál es el problema del siguiente código y cómo lo podemos solucionar para que evalúe a `true`?

   ```
   3 = 3
   ```

4. ¿Qué es la interpolación y para qué se utiliza?
