# Métodos

Eventualmente vas tener algunas líneas de código que necesitan ser ejecutadas varias veces y desde diferentes partes de tu programa. En vez de repetir el mismo código una y otra vez puedes crear un método (también se les conoce como procedimientos o funciones en otros lenguajes de programación) e **invocarlo** cada vez que necesites ejecutar ese trozo de código.

Crea un archivo llamado `methods.rb` y escribe lo siguiente:

```ruby
def hello
  puts "Hola mundo"
end
```

Para definir un método usamos la palabra reservada `def` y le damos un nombre (en este caso `hello`). Al final debemos cerrar el método con `end`.

```
$ ruby methods.rb
```

Si lo ejecutas no debería salir nada. Una característica de los métodos es que no son ejecutados hasta que no los **invoquemos**. Modifiquemos nuestro programa para invocarlo:

```ruby
def hello
  puts "Hola mundo"
end

hello() # acá lo invocamos, los paréntesis son opcionales
```

En la última línea lo estamos invocando. Si lo ejecutas ahora si debería aparecer "Hola mundo":

```
$ ruby methods.rb
Hola mundo
```

## Parámetros

Los métodos pueden recibir cero o más parámetros (o argumentos). Modifiquemos nuestro programa para que salude a cualquier persona:

```ruby
def hello(name)
  puts "Hola #{name}"
end

hello("Germán")
hello("David")
```

Si lo ejecutamos deberías ver lo siguiente:

```
$ ruby methods.rb
Hola Germán
Hola David
```

## Retornando un valor

En Ruby todas las expresiones retornan un valor. Incluso `puts "Hola mundo"` retorna un valor, solo que el valor es `nil` (una forma de decir "nada").

Por defecto, todos los métodos retornan el resultado de la última línea que se ejecute en el método. Vamos a modificar nuestro ejemplo para que en vez de imprimir el saludo, lo retorne:

```ruby
def hello(name)
  "Hola #{name}"
end

puts hello("Germán")
puts hello "David"  # los paréntesis son opcionales
```

Fíjate que ya no hacemos el `puts` dentro de la función, así que nos toca hacerlo al invocar el método. Pero es mejor práctica así. El problema es que cuando el `puts` está dentro de la función, esa función solo nos serviría en aplicaciones de consola. Si la queremos usar en una aplicación Web no serviría (el puts es únicamente para imprimir en la consola).


```
$ ruby methods.rb
Hola Germán
Hola David
```

También es posible retornar el valor explícitamente con la palabra reservada `return`:

```ruby
def hello(name)
  return "Hola #{name}"
end

puts hello("Germán")
puts hello "David"
```

El resultado cuando lo ejecutes debe seguir siendo el mismo.

En general, los programadores de Ruby tienden a omitir el `return` a menos de que sea completamente necesario.

## Un ejemplo

Hagamos un programa que nos diga de qué generación somos dependiendo de nuestro año de nacimiento. Las generaciones son las siguientes:

```
Nacidos <= 1945 - la gran generación
Nacidos entre 1946 y 1964 - baby boomers
Nacidos entre 1965 y 1982 - generación x
Nacidos entre 1983 y 2004 - milenials
Nacidos >= 2005 - centenials
```

Vamos ahora a hacer un método que nos diga la generación y lo invocamos con lo que ingrese el usuario. Crea un archivo llamado `generation_method.rb` y escribe lo siguiente:

```ruby
def generation(year_of_birth)
  if year_of_birth >= 1996
    puts "Eres un centenial"
  elsif year_of_birth >= 1977
    puts "Eres un millenial"
  elsif year_of_birth >= 1965
    puts "Eres generación X"
  elsif year_of_birth >= 1946
    puts "Eres baby boomer"
  else
    puts "Eres tradicionalista"
  end
end

print "¿Cuál es tu año de nacimiento? "
year_of_birth = gets.chomp.to_i
generation(year_of_birth)
```

Si la ejecutas debería decirte la generación dependiendo de tu año de nacimiento:

```
$ ruby generation_method.rb
¿Cuál es tu año de nacimiento? 1982
Eres un millenial
```

Sin embargo, sería mucho mejor evitar el `puts` en el método. Modifiquémoslo para mejorarlo:

```ruby
def generation(year_of_birth)
  if year_of_birth >= 1996
    "Eres un centenial"
  elsif year_of_birth >= 1977
    "Eres un millenial"
  elsif year_of_birth >= 1965
    "Eres generación X"
  elsif year_of_birth >= 1946
    "Eres baby boomer"
  else
    "Eres tradicionalista"
  end
end

print "¿Cuál es tu año de nacimiento? "
year_of_birth = gets.chomp.to_i

puts generation(year_of_birth)
```

Mucho mejor. Sin embargo hay algo que no me gusta de este método. Está retornando los strings en Español. Si quisiéramos comparar ese valor para realizar alguna acción dependiendo de la generación, nos tocaría comparar el string exacto. Además, si queremos tener una aplicación que soporte varios idiomas esta implementación no va a funcionar. Podemos mejorarla:

```ruby
def generation(year_of_birth)
  if year_of_birth >= 1996
    :centenial
  elsif year_of_birth >= 1977
    :millenial
  elsif year_of_birth >= 1965
    :generation_x
  elsif year_of_birth >= 1946
    :baby_boomer
  else
    :traditionalist
  end
end

translations = { centenial: "centenial", millenial: "millenial", generation_x: "X",
  baby_boomer: "baby boomer", traditionalist: "tradicionalista" }

print "¿Cuál es tu año de nacimiento? "
year_of_birth = gets.chomp.to_i

generation_code = generation(year_of_birth)
puts "Eres de la generación #{translations[generation_code]}"
```

El programa es más largo pero la función `generation` es ahora mucho más reutilizable. Si queremos tomar una desición dependiendo de la generación lo podemos hacer fácilmente (comparar símbolos es mucho menos propenso a errores que comparar cadenas de texto).

## Evalúate

1. Escribe un método llamado `square_perimeter` que reciba un argumento `side` y calcule el perímetro de un cuadrado (recuerda que el perímetro de un cuadrado es la suma de los lados). Por ejemplo:

    ```ruby
    square_perimeter(2) # Debería retornar 8
    square_perimeter(5) # Debería retornar 20
    ```

2. Escribe un método llamado `square_area` que reciba un argumento `side` y retorne el área de de un cuadrado. Por ejemplo:

    ```ruby
    square_area(2) # Debería retornar 4
    square_area(5) # Debería retornar 25
    ```

3. Escribe un método llamado `sum` que reciba un arreglo y retorne la suma de los elementos. Por ejemplo:

    ```ruby
    sum([]) # debería retornar 0
    sum([1]) # debería retornar 1
    sum([1, 2, 3]) # debería retornar 6
    ```

4. Escribe un método llamado `average` que reciba un arreglo y retorne el promedio de los elementos. Por ejemplo:

    ```ruby
    average([]) # debería retornar 0
    average([1]) # debería retornar 1
    average([1, 2, 3]) # debería retornar 2
    ```
