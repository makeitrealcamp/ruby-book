# Arreglos

Hasta ahora hemos trabajado con cadenas de texto, números y true/false. En este capítulo vamos a hablar de un nuevo tipo de datos: los arreglos.

Un arreglo es una lista ordenada de elementos de cualquier tipo. Para crear tu primer arreglo crea un archivo llamado `arrays.rb` y escribe lo siguiente:

```ruby
array = [1, "Pedro", true, false, "Juan"]
```

La sintaxis de un arreglo es muy simple. Los elementos del arreglo se envuelven entre corchetes y se separan con coma. Fíjate que el arreglo que creamos contiene números, cadenas de texto, `true` y `false`. Cada elemento del arreglo puede ser de cualquier tipo (incluso otros arreglos!).

## Obteniendo elementos del arreglo

Ahora modifiquemos el programa para que imprima el primer elemento del arreglo:

```ruby
array = [1, "Pedro", true, false, "Juan"]
puts array[0]
```

Ejecútalo:

```shell
$ ruby arrays.rb
1
```

La sintaxis para obtener un elemento del arreglo es `[n]` donde `n` es la posición empezando en 0. Modifica el archivo para imprimir los demás elementos:

```ruby
array = [1, "Pedro", true, false, "Juan"]
puts array[0]
puts array[1]
puts array[2]
puts array[3]
puts array[4]
```

Al ejecutarlo nuevamente deberían aparecer cada uno de los elementos:

```shell
$ ruby arrays.rb
1
Pedro
true
false
Juan
```

## Recorriendo un arreglo

En el ejemplo anterior pudimos imprimir cada una de las posiciones porque era un arreglo de pocos elementos. Sin embargo esto no siempre es práctico. Primero, el arreglo puede ser muy grande o puede que no sepamos el tamaño del arreglo. Modifiquemos el programa anterior para recorrer el arreglo e imprimir todas sus posiciones:

```ruby
array = [1, "Pedro", true, false, "Juan"]

array.each do |element|
  puts element
end
```

El resultado debe ser el mismo que antes, pero esta vez utilizamos un ciclo para recorrer el arreglo en vez de imprimir cada posición. Fíjate que ya no utilizamos la notación `[n]` y la razón es que el método `each` que utilizamos para recorrer el arreglo nos entrega es el **valor** de cada una de las posiciones.

Si necesitamos el índice de cada elemento podemos utilizar el método `each_with_index` en vez de `each`:

```ruby
array = [1, "Pedro", true, false, "Juan"]

array.each_with_index do |element, index|
  puts "#{index}: #{element}"
end
```

El resultado cuando lo ejecutamos debe ser el siguiente:

```shell
$ ruby arrays.rb
0: 1
1: Pedro
2: true
3: false
4: Juan
```

## Reemplazando un elemento

Es posible reemplazar el valor de cualquier elemento del arreglo. Por ejemplo:

```ruby
array = [1, "Pedro", true, false, "Juan"]
array[1] = "Germán" # reemplazamos el elemento en la posición 1

# [1, "Germán", true, false, "Juan"]
```

## Insertando nuevos elementos

Es posible insertar nuevos elementos en un arreglo (puede estar vacío o tener elementos). Por ejemplo:

```ruby
array = ["Pedro"]
array.push("Germán") # ["Pedro", "Germán"]
array << "Diana" # ["Pedro", "Germán", "Diana"]
```

Tanto el método `push` como el operador `<<` funcionan igual para agregar un elemento al final de la lista. ¿Qué pasa si queremos agregar un elemento en la mitad? Para eso sirve el método `insert`:

```ruby
array = ["Pedro", "Germán", "Diana"]
array.insert(0, "Juan") # ["Juan", "Pedro", "Germán", "Diana"]
```

El método `insert` recibe 2 argumentos: la posición en la que se quiere insertar el elemento y el valor del nuevo elemento. Todos los elementos desde esa posición se mueven a la derecha.

## Un ejemplo

Pongamos en práctica lo que hemos visto hasta ahora y creemos un programa que le permita al usuario ingresar un número de personas y seleccione una al azar. Crea un archivo llamado `choose.rb` y escribe lo siguiente:

```ruby
print "Ingresa el número de personas que participarán: "
num = gets.chomp.to_i

people = []
num.times do
  print "Ingresa el nombre de la persona: "
  people << gets.chomp # insertamos cada persona en el arreglo
end

puts "La persona seleccionada es #{people.sample}"
```

Las primeras dos líneas obtienen el número de personas que el usuario quiere ingresar. Después creamos un arreglo vacío en el que vamos a ir agregando las personas. Utilizando el ciclo `times` le pedimos el usuario que ingrese el nombre de cada persona. Por último, seleccionamos un elemento del arreglo al azar utilizando el método `sample`.

Ejecutemos el archivo y probémoslo:

```shell
$ ruby choose.rb
Ingresa el número de personas que participarán: 3
Ingresa el nombre de la persona: Pedro
Ingresa el nombre de la persona: Juan
Ingresa el nombre de la persona: Germán
La persona seleccionada es Pedro
```

# Métodos útiles

Ya hemos visto métodos como `push` para insertar, `each` para recorrer y `sample` para seleccionar un elemento de forma aleatoria en los arreglos. Otros métodos útiles son:

| Método   | Descripción |
|---|---|
| first    | Retorna el primer elemento del arreglo |
| last     | Retorna el último elemento del arreglo |
| shuffle  | Retorna un nuevo arrego mezclado aleatoriamente |
| length   | Retorna el tamaño del arreglo |
| delete_at | Elimina el elemento en la posición especificada |

Puedes ver todos los métodos en la [documentación de Array](https://ruby-doc.org/core-2.3.1/Array.html).

# Métodos con exclamación al final

En la documentación vas a encontrar algunos métodos que terminan con un signo de exclamación al final como `shuffle!` y `reverse!`. Esos métodos se deben utilizar con cuidado porque modifican el arreglo original. Generalmente estos métodos tienen una versión sin signo de exclamación al final que retornan un nuevo arreglo sin modificar el original (p.e. `shuffle` y `reverse`).

En general intenta utilizar los métodos que **no** tienen el signo de exclamación al final a menos de que sea necesario modificar el arreglo original.

Por ejemplo, si quieres mezclar los lementos de un arreglo puedes hacerlo de dos formas:

```ruby
array = [1, 2, 3, 4, 5]

array.shuffle! # modifica el arreglo original
another_array = array.suffle # no modifica el arreglo original
```
