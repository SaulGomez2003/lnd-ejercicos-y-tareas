## Ejercicio 1: Generar mediante XSLT una lista HTML desordenada `<ul>` con los nombres de las frutas.
### XML de entrada:

<fruits>
  <fruit>Apple</fruit>
  <fruit>Banana</fruit>
  <fruit>Cherry</fruit>
</fruits>

### XSLT
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="html"/>
  
  <xsl:template match="/">
    <ul>
      <xsl:for-each select="fruits/fruit">
        <li><xsl:value-of select="."/></li>
      </xsl:for-each>
    </ul>
  </xsl:template>
</xsl:stylesheet>
### Resultado

<ul>
  <li>Apple</li>
  <li>Banana</li>
  <li>Cherry</li>
</ul>

## Ejercicio 2: Crear una tabla HTML de libros con las columnas "Título" y "Autor".

### XML de entrada:

<library>
  <book>
    <title>1984</title>
    <author>George Orwell</author>
  </book>
  <book>
    <title>Brave New World</title>
    <author>Aldous Huxley</author>
  </book>
</library>

### XSLT

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="html"/>
  
  <xsl:template match="/">
    <table border="1">
      <tr>
        <th>Title</th>
        <th>Author</th>
      </tr>
      <xsl:for-each select="library/book">
        <tr>
          <td><xsl:value-of select="title"/></td>
          <td><xsl:value-of select="author"/></td>
        </tr>
      </xsl:for-each>
    </table>
  </xsl:template>
</xsl:stylesheet>

### Resultado

<table border="1">
  <tr>
    <th>Title</th>
    <th>Author</th>
  </tr>
  <tr>
    <td>1984</td>
    <td>George Orwell</td>
  </tr>
  <tr>
    <td>Brave New World</td>
    <td>Aldous Huxley</td>
  </tr>
</table>

## Ejercicio 3: Crear un fichero HTML con un encabezado en cada sección. Generar encabezados `<h2>` y párrafos `<p>` para cada sección.

### XML de entrada:

<sections>
  <section>
    <title>Introduction</title>
    <content>Welcome to the tutorial.</content>
  </section>
  <section>
    <title>Chapter 1</title>
    <content>This is the first chapter.</content>
  </section>
</sections>

### XLST

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="html"/>
  
  <xsl:template match="/">
    <xsl:for-each select="sections/section">
      <h2><xsl:value-of select="title"/></h2>
      <p><xsl:value-of select="content"/></p>
    </xsl:for-each>
  </xsl:template>
</xsl:stylesheet>

### Resultado

<h2>Introduction</h2>
<p>Welcome to the tutorial.</p>
<h2>Chapter 1</h2>
<p>This is the first chapter.</p>

## Ejercicio 4: Generar un fichero HTML donde se resalten los productos con precio mayor a 500 en negrita `<b>`.

### XML de entrada:

<products>
  <product>
    <name>Laptop</name>
    <price>1000</price>
  </product>
  <product>
    <name>Mouse</name>
    <price>25</price>
  </product>
</products>

### XLST

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="html"/>
  
  <xsl:template match="/">
    <xsl:for-each select="products/product">
      <p>
        <xsl:if test="price &gt; 500">
          <b><xsl:value-of select="name"/> - $<xsl:value-of select="price"/></b>
        </xsl:if>
        <xsl:if test="price &lt;= 500">
          <xsl:value-of select="name"/> - $<xsl:value-of select="price"/>
        </xsl:if>
      </p>
    </xsl:for-each>
  </xsl:template>
</xsl:stylesheet>

### Resultado

<p><b>Laptop</b> - $1000</p>
<p>Mouse - $25</p>

## Ejercicio 5: Generar un fichero HTML con una lista de navegación `<nav>`.

### XML de entrada:

<menu>
  <item>Home</item>
  <item>About</item>
  <item>Contact</item>
</menu>

### XSLT

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="html"/>
  
  <xsl:template match="/">
    <nav>
      <ul>
        <xsl:for-each select="menu/item">
          <li><xsl:value-of select="."/></li>
        </xsl:for-each>
      </ul>
    </nav>
  </xsl:template>
</xsl:stylesheet

### Resultado

<nav>
  <ul>
    <li>Home</li>
    <li>About</li>
    <li>Contact</li>
  </ul>
</nav>

## Ejercicio 6: Generar un fichero JSON con la lista de frutas.

### XML de entrada:

<fruits>
  <fruit>Apple</fruit>
  <fruit>Banana</fruit>
  <fruit>Cherry</fruit>
</fruits>

### XSLT

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="text"/>
  
  <xsl:template match="/">
    [
      <xsl:for-each select="fruits/fruit">
        <xsl:value-of select="."/>, 
      </xsl:for-each>
    ]
  </xsl:template>
</xsl:stylesheet>

### Resultado

[
  "Apple",
  "Banana",
  "Cherry"
]

## Ejercicio 7: Crear un fichero JSON con los productos y sus respectivos precios.

### XML de entrada:

<products>
  <product>
    <name>Laptop</name>
    <price>1000</price>
  </product>
  <product>
    <name>Mouse</name>
    <price>25</price>
  </product>
</products>

### XLST

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="text"/>
  
  <xsl:template match="/">
    [
      <xsl:for-each select="products/product">
        <xsl:text>{</xsl:text>
        "name": "<xsl:value-of select="name"/>",
        "price": <xsl:value-of select="price"/>
        <xsl:text>}</xsl:text>
        <xsl:if test="position() != last()">,</xsl:if>
      </xsl:for-each>
      <xsl:text>]</xsl:text>
    </xsl:template>
</xsl:stylesheet>

### Resultado

[
  {
    "name": "Laptop",
    "price": 1000
  },
  {
    "name": "Mouse",
    "price": 25
  }
]

## Ejercicio 8: Crear un Objeto JSON con los nombres de usuarios.

### XML de entrada:

<users>
  <user>
    <id>1</id>
    <name>John Doe</name>
    <email>john@example.com</email>
  </user>
  <user>
    <id>2</id>
    <name>Jane Smith</name>
    <email>jane@example.com</email>
  </user>
</users>

### XSLT

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="text"/>
  
  <xsl:template match="/">
    [
      <xsl:for-each select="users/user">
        <xsl:text>{</xsl:text>
        "id": "<xsl:value-of select="id"/>",
        "name": "<xsl:value-of select="name"/>",
        "email": "<xsl:value-of select="email"/>"
        <xsl:text>}</xsl:text>
        <xsl:if test="position() != last()">,</xsl:if>
      </xsl:for-each>
      <xsl:text>]</xsl:text>
    </xsl:template>
</xsl:stylesheet>

### Resultado

[
  {
    "id": "1",
    "name": "John Doe",
    "email": "john@example.com"
  },
  {
    "id": "2",
    "name": "Jane Smith",
    "email": "jane@example.com"
  }
]

## Ejercicio 9: Crear un fichero JSON con las categorías y los productos.

### XML de entrada:

<store>
  <category name="Electronics">
    <product>
      <name>Laptop</name>
      <price>1000</price>
    </product>
    <product>
      <name>Smartphone</name>
      <price>700</price>
    </product>
  </category>
  <category name="Books">
    <product>
      <name>1984</name>
      <price>15.99</price>
    </product>
    <product>
      <name>Brave New World</name>
      <price>12.49</price>
    </product>
  </category>
</store>

### XSLT

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="text"/>

  <xsl:template match="/">
    {
      <xsl:for-each select="store/category">
        <xsl:value-of select="concat('&quot;', @name, '&quot;', ': [')"/>
        <xsl:for-each select="product">
          <xsl:value-of select="concat('{ &quot;name&quot;: &quot;', name, '&quot;, &quot;price&quot;: ', price, ' }')"/>
          <xsl:if test="position() != last()">, </xsl:if>
        </xsl:for-each>
        <xsl:value-of select="concat(']')"/>
        <xsl:if test="position() != last()">, </xsl:if>
      </xsl:for-each>
    }
  </xsl:template>
</xsl:stylesheet>

### Resultado

{
  "Electronics": [
    {
      "name": "Laptop",
      "price": 1000
    },
    {
      "name": "Smartphone",
      "price": 700
    }
  ],
  "Books": [
    {
      "name": "1984",
      "price": 15.99
    },
    {
      "name": "Brave New World",
      "price": 12.49
    }
  ]
}

## Ejercicio 10: Crear un fichero JSON con los títulos de secciones y su contenido.

### XML de entrada:

<document>
  <section>
    <title>Introduction</title>
    <content>Welcome to this tutorial.</content>
  </section>
  <section>
    <title>Chapter 1</title>
    <content>This is the first chapter.</content>
  </section>
</document>

### XSLT

<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="text"/>

  <xsl:template match="/">
    [
      <xsl:for-each select="document/section">
        <xsl:value-of select="concat('{ &quot;title&quot;: &quot;', title, '&quot;, &quot;content&quot;: &quot;', content, '&quot; }')"/>
        <xsl:if test="position() != last()">, </xsl:if>
      </xsl:for-each>
    ]
  </xsl:template>
</xsl:stylesheet>

### Resultado

[
  {
    "title": "Introduction",
    "content": "Welcome to this tutorial."
  },
  {
    "title": "Chapter 1",
    "content": "This is the first chapter."
  }
]
