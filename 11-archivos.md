# Manipulación de archivos

La manipulación de archivos en Ruby es relativamente fácil a comparación de otros lenguajes. Sin embargo, existen varias formas de hacer lo mismo, así que veremos las más comunes.

## Leer de un archivo

La forma más fácil de leer un archivo es con `File.read`, que retorna un `string` con todo el contenido del archivo.

Por ejemplo, crea un nuevo archivo llamado `contenido.txt` con el siguiente contenido:

```
Primera línea
Segunda línea
Tercera línea
```

Ahora abre IRB **en la misma carpeta donde se encuentra el archivo** y escribe lo siguiente:

```
$ irb
> File.read("contenido.txt")
 => "Primera línea\nSegunda línea\nTercera línea\n"
>
```

Los saltos de línea están representados por el caracter `\n` que puedes utilizar para dividir la cadena en líneas (dentro de un arreglo) y recorrerlas. Por ejemplo:

```ruby
content = File.read("contenido.txt") # lee el archivo
lines = content.split("\n") # divide el contenido en líneas

# recorre las líneas y las imprime
lines.each do |line|
  puts line
end
```

El método `File.readlines` retorna las líneas del archivo en un arreglo:

```ruby
lines = File.readlines("contenido.txt")

lines.each do |line|
  puts line
end
```

### Leyendo archivos grandes

Los métodos `File.read` y `File.readlines` leen todo el archivo en memoria. El problema es que si el archivo es muy grande es posible que la máquina no tenga la suficiente memoria para leerlo.

El método `File.foreach` va leyendo el archivo línea por línea sin necesidad de cargarlo todo en memoria y, en general, es la forma más recomendada de leer archivos de texto:

```ruby
File.foreach("contenido.txt") do |line|
  puts line
end
```

## Escribir a un archivo

La forma más fácil de escribir a un archivo es con el método `File.write` que recibe la ruta del archivo y el contenido.

Por ejemplo, abre IRB y escribe tu primer archivo con Ruby:

```
$ irb
> File.write("cuento.txt", "Había una vez ...")
 => 18
```

El método `File.write` retorna el número de bytes que se escribieron. (Fíjate que la cadena tiene 17 caracteres pero se escribieron 18 bytes, esto se debe a que el caracter `í` ocupa 2 caracteres).

Otra opción es utilizar el método `File.open` que recibe la ruta del archivo, el modo de apertura y un bloque que vamos a utilizar para escribir en el archivo. Por ejemplo:

```ruby
File.open("cuento.txt", "w") do |file|
  file.write("Había una vez ...")
end
```

## Verificar si un archivo o carpeta existe

Para verificar si un archivo o una carpeta existe utiliza el método `File.exist?`:

```ruby
if File.exist?("ruta/al/archivo")
  # código si el archivo o la carpeta existe
else
  # código si el archivo o la carpeta no existe
end
```

Si quieres verificar si un archivo (no carpeta) existe, utiliza el método `File.file?`:

```ruby
if File.exist?("ruta/al/archivo")
  # código si el archivo existe
else
  # código si el archivo no existe
end
```

## Evalúate

1. Escribe un método llamado `save_contacts` que reciba un arreglo de hashes con la información de personas y escriba un archivo separado por comas llamado `contactos.csv`. Por ejemplo:

    ```ruby
    contacts = [
      { id: 1, name: "Pedro Perez", mobile: "123456" },
      { id: 2, name: "Juan Gomez", mobile: "654321" }
    ]  

    save_contacts(contacts) # debería crear un archivo contactos.csv
    ```

    El archivo debería quedar de la siguiente forma:

    ```
    1,Pedro Perez,123456
    2,Juan Gomez,654321
    ```

2. Escribe un método llamado `load_contacts` que cargue la información de personas de un archivo llamado `contactos.csv` y retorne un arreglo de hashes como el del método anterior.

    ```ruby
    load_contacts # debería retornar un arreglo de hashes
    ```

3. Modifica los dos métodos anteriores para que reciban la ruta del archivo que se quiere crear:

    ```ruby
    save_contacts("otros_contactos.csv", contacts)
    load_contacts("otros_contacts.csv")
    ```
