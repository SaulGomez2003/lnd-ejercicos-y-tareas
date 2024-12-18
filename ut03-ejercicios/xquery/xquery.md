# Ejercicios XQuery

## Ejercicio 1: Archivo `biblioteca.xml`

<biblioteca>
  <libro id="1" genero="Ficción">
    <titulo>1984</titulo>
    <autor pais="Reino Unido">George Orwell</autor>
    <precio moneda="USD">19.99</precio>
  </libro>
  <libro id="2" genero="Ciencia Ficción">
    <titulo>Brave New World</titulo>
    <autor pais="Reino Unido">Aldous Huxley</autor>
    <precio moneda="USD">14.99</precio>
  </libro>
  <libro id="3" genero="Distopía">
    <titulo>Fahrenheit 451</titulo>
    <autor pais="EE.UU.">Ray Bradbury</autor>
    <precio moneda="USD">12.50</precio>
  </libro>
  <libro id="4" genero="Ficción">
    <titulo>To Kill a Mockingbird</titulo>
    <autor pais="EE.UU.">Harper Lee</autor>
    <precio moneda="USD">18.99</precio>
  </libro>
  <libro id="5" genero="Ficción">
    <titulo>The Great Gatsby</titulo>
    <autor pais="EE.UU.">F. Scott Fitzgerald</autor>
    <precio moneda="USD">10.99</precio>
  </libro>
</biblioteca>

1. Devuelve todos los títulos de los libros.

for $libro in //libro
return $libro/titulo

2. Devuelve los títulos de libros cuyo precio es mayor a 15.

for $libro in //libro
where $libro/precio > 15
return $libro/titulo

3. Lista los autores y sus países de origen.

for $libro in //libro
return <autor_pais>
         <autor>{$libro/autor/text()}</autor>
         <pais>{$libro/autor/@pais}</pais>
       </autor_pais>

4. Calcula el precio promedio de los libros.

let $precios := //libro/precio
return avg($precios)

5. Devuelve los títulos ordenados alfabéticamente.

for $libro in //libro
order by $libro/titulo
return $libro/titulo

6. Devuelve los títulos y precios de los libros en formato XML.

for $libro in //libro
return <libro>
         <titulo>{$libro/titulo}</titulo>
         <precio>{$libro/precio}</precio>
       </libro>

7. Encuentra libros del género "Ficción".

for $libro in //libro
where $libro/@genero = "Ficción"
return $libro/titulo

8. Devuelve los libros cuyo autor sea de "EE.UU.".

for $libro in //libro
where $libro/autor/@pais = "EE.UU."
return $libro/titulo

9.  Lista los libros y su precio total (precio + 5 USD de impuesto).

for $libro in //libro
let $precio_con_impuesto := $libro/precio + 5
return <libro_con_impuesto>
         <titulo>{$libro/titulo}</titulo>
         <precio_total>{$precio_con_impuesto}</precio_total>
       </libro_con_impuesto>

10. Devuelve el libro más caro en el catálogo.

let $libro_mas_caro := max(//libro/precio)
for $libro in //libro
where $libro/precio = $libro_mas_caro
return $libro/titulo




## Ejercicio 2: Archivo tienda.xml

<tienda>
  <producto id="1" categoria="Computadoras">
    <nombre>Portátil</nombre>
    <marca>HP</marca>
    <precio moneda="USD">800</precio>
  </producto>
  <producto id="2" categoria="Accesorios">
    <nombre>Monitor</nombre>
    <marca>Dell</marca>
    <precio moneda="USD">200</precio>
  </producto>
  <producto id="3" categoria="Accesorios">
    <nombre>Ratón</nombre>
    <marca>Logitech</marca>
    <precio moneda="USD">25</precio>
  </producto>
  <producto id="4" categoria="Computadoras">
    <nombre>Escritorio</nombre>
    <marca>Lenovo</marca>
    <precio moneda="USD">600</precio>
  </producto>
  <producto id="5" categoria="Impresoras">
    <nombre>Impresora</nombre>
    <marca>Canon</marca>
    <precio moneda="USD">150</precio>
  </producto>
</tienda>

1. Devuelve los nombres de todos los productos.

for $producto in //producto
return $producto/nombre

2. Devuelve los productos de la categoría "Accesorios".

for $producto in //producto
where $producto/@categoria = "Accesorios"
return $producto/nombre

3. Calcula el precio total de todos los productos.

let $precios := //producto/precio
return sum($precios)

4. Encuentra productos con un precio mayor a 500 USD.

for $producto in //producto
where $producto/precio > 500
return $producto/nombre

5. Devuelve los productos y sus precios con un descuento del 10%.

for $producto in //producto
let $precio_descuento := $producto/precio * 0.9
return <producto_descuento>
         <nombre>{$producto/nombre}</nombre>
         <precio_con_descuento>{$precio_descuento}</precio_con_descuento>
       </producto_descuento>

6. Lista los productos ordenados por precio de menor a mayor.

for $producto in //producto
order by $producto/precio
return $producto/nombre

7. Devuelve los productos de la marca "HP".

for $producto in //producto
where $producto/marca = "HP"
return $producto/nombre

8. Devuelve los nombres y categorías de los productos como elementos <item>.

for $producto in //producto
return <item>
         <nombre>{$producto/nombre}</nombre>
         <categoria>{$producto/@categoria}</categoria>
       </item>

9.  Encuentra el producto más barato.

let $producto_mas_barato := min(//producto/precio)
for $producto in //producto
where $producto/precio = $producto_mas_barato
return $producto/nombre

10. Calcula el precio promedio de los productos en la categoría "Computadoras".

let $precios_computadoras := //producto[@categoria = "Computadoras"]/precio
return avg($precios_computadoras)

A continuación te proporciono las consultas XQuery para resolver los ejercicios planteados sobre el archivo musica.xml.

## Ejercicio 3: Archivo musica.xml

<catalogo>
  <album id="1" genero="Rock">
    <titulo>The Dark Side of the Moon</titulo>
    <artista>Pink Floyd</artista>
    <anio>1973</anio>
    <precio>20.00</precio>
  </album>
  <album id="2" genero="Pop">
    <titulo>Thriller</titulo>
    <artista>Michael Jackson</artista>
    <anio>1982</anio>
    <precio>18.00</precio>
  </album>
  <album id="3" genero="Rock">
    <titulo>Abbey Road</titulo>
    <artista>The Beatles</artista>
    <anio>1969</anio>
    <precio>25.00</precio>
  </album>
  <album id="4" genero="Jazz">
    <titulo>Kind of Blue</titulo>
    <artista>Miles Davis</artista>
    <anio>1959</anio>
    <precio>15.00</precio>
  </album>
</catalogo> 

1. Devuelve todos los títulos de los álbumes.

for $album in //album
return $album/titulo

2. Devuelve los álbumes cuyo precio es mayor a 18.

for $album in //album
where $album/precio > 18
return $album/titulo

3. Lista los títulos y géneros de todos los álbumes.

for $album in //album
return <album_info>
         <titulo>{$album/titulo}</titulo>
         <genero>{$album/@genero}</genero>
       </album_info>

4. Calcula el precio promedio de los álbumes (usa let).

let $precios := //album/precio
return avg($precios)

5. Encuentra los álbumes de género "Rock".

for $album in //album
where $album/@genero = "Rock"
return $album/titulo

6. Ordena los álbumes por año de lanzamiento.

for $album in //album
order by $album/anio
return $album/titulo

7. Devuelve el álbum más caro.

let $album_mas_caro := max(//album/precio)
for $album in //album
where $album/precio = $album_mas_caro
return $album/titulo

8. Devuelve los títulos y los precios con un descuento del 20%.

for $album in //album
let $precio_descuento := $album/precio * 0.8
return <album_descuento>
         <titulo>{$album/titulo}</titulo>
         <precio_con_descuento>{$precio_descuento}</precio_con_descuento>
       </album_descuento>

9.  Devuelve los álbumes lanzados antes de 1975.

for $album in //album
where $album/anio < 1975
return $album/titulo

10. Calcula el precio total de todos los álbumes.

let $precios := //album/precio
return sum($precios)

## Ejercicio 4: Archivo estudiantes.xml

<estudiantes>
  <estudiante id="1" carrera="Ingeniería">
    <nombre>Juan</nombre>
    <edad>20</edad>
    <nota>8.5</nota>
  </estudiante>
  <estudiante id="2" carrera="Derecho">
    <nombre>María</nombre>
    <edad>22</edad>
    <nota>9.0</nota>
  </estudiante>
  <estudiante id="3" carrera="Medicina">
    <nombre>Pedro</nombre>
    <edad>19</edad>
    <nota>7.5</nota>
  </estudiante>
  <estudiante id="4" carrera="Ingeniería">
    <nombre>Ana</nombre>
    <edad>21</edad>
    <nota>8.8</nota>
  </estudiante>
</estudiantes>

1. Devuelve los nombres de los estudiantes.

for $estudiante in //estudiante
return $estudiante/nombre

2. Filtra los estudiantes con una nota mayor a 8.

for $estudiante in //estudiante
where $estudiante/nota > 8
return $estudiante/nombre

3. Devuelve los nombres y las carreras de los estudiantes.

for $estudiante in //estudiante
return <estudiante_info>
         <nombre>{$estudiante/nombre}</nombre>
         <carrera>{$estudiante/@carrera}</carrera>
       </estudiante_info>

4. Calcula la nota promedio de los estudiantes (usa let).

let $notas := //estudiante/nota
return avg($notas)

5. Devuelve los estudiantes de la carrera "Ingeniería".

for $estudiante in //estudiante
where $estudiante/@carrera = "Ingeniería"
return $estudiante/nombre

6. Ordena a los estudiantes por edad.

for $estudiante in //estudiante
order by $estudiante/edad
return $estudiante/nombre

7. Devuelve el estudiante más joven.

let $edad_mas_joven := min(//estudiante/edad)
for $estudiante in //estudiante
where $estudiante/edad = $edad_mas_joven
return $estudiante/nombre

8. Devuelve los nombres y las notas incrementadas en 0.5.

for $estudiante in //estudiante
let $nota_incrementada := $estudiante/nota + 0.5
return <estudiante_con_nota_incrementada>
         <nombre>{$estudiante/nombre}</nombre>
         <nota_incrementada>{$nota_incrementada}</nota_incrementada>
       </estudiante_con_nota_incrementada>

9.  Devuelve los estudiantes cuya nota es mayor a 8 y pertenecen a Ingeniería.

for $estudiante in //estudiante
where $estudiante/nota > 8 and $estudiante/@carrera = "Ingeniería"
return $estudiante/nombre

10. Cuenta cuántos estudiantes hay en total.

count(//estudiante)

## Ejercicio 5: Archivo pedidos.xml

<pedidos>
  <pedido id="1" cliente="Juan">
    <producto>Televisor</producto>
    <cantidad>1</cantidad>
    <precio>400</precio>
  </pedido>
  <pedido id="2" cliente="María">
    <producto>Teléfono</producto>
    <cantidad>2</cantidad>
    <precio>200</precio>
  </pedido>
  <pedido id="3" cliente="Pedro">
    <producto>Ratón</producto>
    <cantidad>5</cantidad>
    <precio>25</precio>
  </pedido>
  <pedido id="4" cliente="Ana">
    <producto>Teclado</producto>
    <cantidad>3</cantidad>
    <precio>30</precio>
  </pedido>
</pedidos>

1. Devuelve los nombres de los clientes.

for $pedido in //pedido
return $pedido/@cliente

2. Devuelve los productos con precio total (cantidad × precio).

for $pedido in //pedido
let $precio_total := $pedido/cantidad * $pedido/precio
return <producto_precio_total>
         <producto>{$pedido/producto}</producto>
         <precio_total>{$precio_total}</precio_total>
       </producto_precio_total>

3. Filtra los pedidos cuyo precio total sea mayor a 100.

for $pedido in //pedido
let $precio_total := $pedido/cantidad * $pedido/precio
where $precio_total > 100
return $pedido/producto

4. Calcula el precio promedio de todos los pedidos.

let $precio_totales := //pedido/cantidad * //pedido/precio
return avg($precio_totales)

5. Devuelve el pedido más caro.

let $precio_totales := //pedido/cantidad * //pedido/precio
let $pedido_mas_caro := max($precio_totales)
for $pedido in //pedido
where $pedido/cantidad * $pedido/precio = $pedido_mas_caro
return $pedido/producto

6. Ordena los pedidos por cliente alfabéticamente.

for $pedido in //pedido
order by $pedido/@cliente
return $pedido/producto

7. Calcula el precio total de todos los pedidos.

let $precio_totales := //pedido/cantidad * //pedido/precio
return sum($precio_totales)

8. Devuelve los nombres de los clientes que compraron más de 3 unidades.

for $pedido in //pedido
where $pedido/cantidad > 3
return $pedido/@cliente

9.  Devuelve los productos y sus precios con un descuento del 15% (usa let).

for $pedido in //pedido
let $precio_descuento := $pedido/precio * 0.85
return <producto_descuento>
         <producto>{$pedido/producto}</producto>
         <precio_con_descuento>{$precio_descuento}</precio_con_descuento>
       </producto_descuento>

10. Cuenta el número total de pedidos.

count(//pedido)
