## Ejercico 1
1. Selecciona todos los títulos de los libros
   
   //book/title
2. Selecciona los autores de los libros en el género "Programming".
   
   //book[genre="Programming"]/author
3. Selecciona el precio del libro "The Art of War".
   
   //book[title="The Art of War"]/price
4. Cuenta cuántos libros tienen más de 20 en stock.
   
   count(//book[stock > 20])
5. Selecciona todos los géneros únicos disponibles en la tienda.
   
   //book/genre
6. Selecciona el autor cuyo libro cuesta más.
   
   //book[price = max(//book/price)]/author
7. Selecciona el título del libro más barato.
   
   //book[price = min(//book/price)]/title
8. Selecciona todos los libros cuyo precio esté entre 10 y 30.
   
   //book[price >= 10 and price <= 30]
9.  Selecciona todos los libros que tengan menos de 20 unidades en stock.
    
    //book[stock < 20]
10. Selecciona el atributo id de todos los libros.
    
    //book/@id
## Ejercico 2
1. Selecciona todos los nombres de productos.
   
   //item/name
2. Selecciona los productos de la marca "BrandX".
   
   //item[brand="BrandX"]
3. Selecciona el producto más barato.
   
   //item[price = (//item/price)[min(//item/price)]]
4. Selecciona el producto más caro.
   
   //item[price = (//item/price)[max(//item/price)]]
5. Selecciona los nombres y precios de productos con más de 30 unidades en stock.
   
   //item[stock > 30]/name | //item[stock > 30]/price
6. Selecciona el atributo currency de todos los precios.
   
   //item/price/@currency
7. Cuenta cuántos productos hay en stock con menos de 20 unidades.
   
   count(//item[stock < 20])
8. Selecciona los nombres de todos los productos cuyo precio sea mayor a 500.
   
   //item[price > 500]/name
9.  Selecciona los nombres de productos con el atributo id mayor a 202.
    
    //item[@id > 202]/name
10. Selecciona todos los nodos completos de productos con "BrandZ".
    
    //item[brand="BrandZ"]
## Ejercico 3
1. Selecciona todos los títulos de los libros.
   
   //book/title
2. Selecciona todos los libros disponibles (con available="true").
   
   //book[available="true"]
3. Selecciona el autor del libro "1984".
   
   //book[title="1984"]/author
4. Selecciona todos los géneros de libros únicos.
   
   //book/genre
5. Cuenta cuántos libros están disponibles.
   
   count(//book[available="true"])
6. Selecciona los títulos de los libros que no están disponibles.
   
   //book[available="false"]/title
7. Selecciona los autores cuyos libros están disponibles.
   
   //book[available="true"]/author
8. Selecciona el ID del libro "The Great Gatsby".
   
   //book[title="The Great Gatsby"]/@id
9.  Selecciona todos los libros del género "Fiction".
    
    //book[genre="Fiction"]
10. Selecciona los títulos de los libros cuyo autor es "Herman Melville".
    
    //book[author="Herman Melville"]/title
## Ejercico 4
1. Selecciona todos los títulos de los álbumes.
   
   //album/title
2. Selecciona los títulos de los álbumes del género "Rock".
   
   //album[genre="Rock"]/title
3. Selecciona el precio del álbum "21".
   
   //album[title="21"]/price
4. Cuenta cuántos álbumes tienen más de 20 en stock.
   
   count(//album[stock > 20])
5. Selecciona los nombres de los artistas cuyos álbumes cuestan más de 18 USD.
   
   //album[price > 18]/artist
6. Selecciona el álbum más caro.
   
   //album[price = (//album/price)[max(//album/price)]]
7. Selecciona el género del álbum "Thriller".
   
   //album[title="Thriller"]/genre
8. Selecciona el ID de todos los álbumes de la artista "Adele".
   
   //album[artist="Adele"]/@id
9.  Selecciona los álbumes con menos de 30 en stock.
    
    //album[stock < 30]
10. Selecciona todos los géneros únicos disponibles.
    
    //album/genre
## Ejercico 5
1. Selecciona los nombres de todos los productos.
   
   //product/name
2. Selecciona todos los productos de la categoría "Furniture".
   
   //product[category="Furniture"]
3. Selecciona el precio del producto "Lamp".
   
   //product[name="Lamp"]/price
4. Cuenta cuántos productos tienen más de 50 en stock.
   
   count(//product[stock > 50])
5. Selecciona el producto más caro.
   
   //product[price = (//product/price)[max(//product/price)]]
6. Selecciona los nombres de los productos con menos de 30 en stock.
   
   //product[stock < 30]/name
7. Selecciona todos los precios en USD.
   
   //product/price[@currency="USD"]
8. Selecciona el ID de todos los productos de la categoría "Lighting".
   
   //product[category="Lighting"]/@id
9.  Selecciona el precio del producto más barato.
    
    //product[price = (//product/price)[min(//product/price)]]
   
10. Selecciona los nombres y precios de todos los productos ordenados por precio.
    
    //product/name | //product/price