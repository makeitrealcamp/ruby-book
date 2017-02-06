# Hashes

El último tipo de datos que vamos a ver son los hashes (no encontré una buena traducción al español). Un hash es una colección de datos en donde cada valor está asociado a una llave. Imagina un diccionario, en donde las palabras son las llaves y las deficiones son los valores.

Abramos IRB y creemos nuestro primer hash:

```
$ irb
2.3.1 :001 > humanoide1 = {"nombre" => "Germán", "apellido" => "Escobar", "edad" => 34, "estatura" => 1.8}
 => {"nombre"=>"Germán", "apellido"=>"Escobar", "edad"=>34, "estatura"=>1.8}
```

En este ejemplo utilizamos un hash para almacenar la información de un humano, pero podemos utilizar los hashes para almacenar cualquier tipo de información que requiera esa asociación llave-valor.

Para obtener el valor de una llave utilizamos una notación muy similar a como lo hacíamos con los arreglos:

```
2.3.1 :002 > humanoide1["nombre"]
 => "Germán"
```

Sin embargo, en vez de utilizar la posición como en los arreglos, utilizamos la llave. Las llaves pueden ser de cualquier tipo. En el ejemplo anterior utilizamos strings pero también podrían ser números:

```
2.3.1 :003 > statuses = {0 => "encendido", 1 => "apagado", 2 => "fundido"}
 => {0 => "encendido", 1 => "apagado", 2 => "fundido"}
```

Y para obtener el valor de alguna llave:

```
2.3.1 :004 > statuses[1]
 => "apagado"
```

## Usando símbolos como llaves

En los ejemplos anteriores hemos usado cadenas de texto y números como llaves de los hashes. Sin embargo, en Ruby hay un tipo de datos que es muy utilizado como llaves en los hashes: los símbolos.

```ruby
status = :encendido # nuestro primer símbolo
```

Los símbolos son muy parecidos a las cadenas de texto pero con las siguientes diferencias:

* No están envueltos en comillas.
* Empiezan con dos puntos (:).
* No contienen espacios en blanco.

Creemos nuestro primer hash con símbolos:

```
$ irb
2.3.1 :001 > humaniode1 = {:nombre => "Germán", :apellido => "Escobar", :edad => 34, :estatura => 1.8}
```

Muy parecido al ejemplo anterior. Pero entonces ¿cuál es la ventaja de usar símbolos como llaves de un hash? La respuesta es que cuando usamos símbolos podemos escribir los hashes de forma más corta:

```
2.3.1 :002 > humaniode1 = {nombre: "Germán", apellido: "Escobar", edad: 34, estatura: 1.8}
```

Los cambios que hicimos son los siguientes:

* Eliminamos el `=>` (hash rocket)
* Movimos los dos puntos (:) al final del símbolo.

Para obtener algún valor del hash utilizamos el símbolo:

```
2.3.1 :003 > humaniode1[:nombre]
 => "Germán"
```

## Mezclando arreglos y hashes

Es posible mezclar arreglos y hashes para crear estructuras complejas. Para probar crea un archivo llamado `products.rb` y escribe lo siguiente:

```ruby
products = [
  { id: 1, name: "Leche", price: 120, categories: ["familiar", "comida"] },
  { id: 2, name: "Arroz", price: 80, ["familiar", "comida"] },
  { id: 3, name: "Lavadora", price: 7800, categories: ["electrodomésticos"] }
]
```

En este ejemplo hemos creado un arreglo de hashes. Cada hash representa un producto y una de sus llaves (`:categories`) contiene un arreglo. Modifiquemos el programa para imprimir los productos en la consola:

```ruby
products = [
  { id: 1, name: "Leche", price: 120, categories: ["familiar", "comida"] },
  { id: 2, name: "Arroz", price: 80, ["familiar", "comida"] },
  { id: 3, name: "Lavadora", price: 7800, categories: ["electrodomésticos"] }
]

products.each do |product|
  puts product[:name]
  puts "  Id: #{product[:id]}"
  puts "  Precio: #{product[:name]}"
  puts "  Categorias: #{product[:categories].join(", ")}"
  puts "-" * 20
end
```

Lo primero que estamos haciendo es iterando por el arreglo de productos. Por cada uno de los productos (recuerda que esto es un hash) vamos a mostrar el nombre (la llave `:nombre`), después el identificador (la llave `:id`), el precio (la llave `:price`) y las categorías (la llave `:categories`). Como las categorías están en un arreglo debemos utilizar el método `join` para convertirlas en una cadena.
