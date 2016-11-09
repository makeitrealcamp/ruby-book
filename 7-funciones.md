# Métodos

Eventualmente vas tener algunas líneas de código que necesitan ser ejecutadas varias veces y desde diferentes partes de tu programa. En vez de repetir el mismo código una y otra vez puedes crear un método (también se les conoce como procedimientos o funciones en otros lenguajes de programación) e **invocarlo** cada vez que necesites ejecutar ese trozo de código.

Crea un archivo llamado `methods.rb` y escribe lo siguiente:

```ruby
def hello
  puts "Hola mundo"
end
```

Para definir un método usamos la palabra reservada `def` y le damos un nombre (en este caso hello). Al final debemos cerrar el método con `end`.

```shell
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

```shell
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

```shell
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


```shell
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

Vamos a crear un método que reciba un número 
