# Imágenes

Las imágenes pueden mostrarse usando la etiqueta `img`.

Esta etiqueta acepta un atributo `src`, que se utiliza para indicar la fuente de la imagen:

```html
<img src="image.png">
```

Podemos utilizar una amplia variedad de formatos de imagen. Los más comunes son PNG, JPEG, GIF, SVG y, más recientemente, WebP.

El estándar HTML requiere que el atributo `alt` esté presente para describir el contenido de la imagen. Este atributo es utilizado tanto por los lectores de pantalla como por los motores de búsqueda:

```html
<img src="dog.png" alt="Una foto de un perro">
```

También puede establecer los atributos `width` y `height` para reservar el espacio que ocupará la imagen. De esta forma, el navegador puede calcular el diseño de la página antes de que la imagen termine de cargarse, evitando cambios inesperados en la interfaz. Ambos atributos reciben un valor numérico expresado en píxeles.

```html
<img src="dog.png" alt="Una foto de un perro" width="300" height="200">
```

## La etiqueta `figure`

La etiqueta `figure` suele utilizarse junto con la etiqueta `img`.

`figure` es una etiqueta semántica que se emplea cuando se desea mostrar una imagen acompañada de un pie de foto. Se utiliza de la siguiente manera:

```html
<figure>
    <img src="dog.png"
         alt="Un buen chico">
    <figcaption>Un buen chico</figcaption>
</figure>
```

La etiqueta `figcaption` define el pie de foto de la imagen.

## Imágenes responsivas con `srcset`

El atributo `srcset` permite configurar imágenes responsivas para que el navegador seleccione la versión más adecuada según la densidad de píxeles o el tamaño de la ventana. De este modo, solo descargará la imagen que realmente necesite, evitando cargar imágenes de gran tamaño en dispositivos pequeños.

Este es un ejemplo en el que se proporcionan cuatro versiones de la misma imagen para distintos tamaños de pantalla:

```html
<img src="dog.png"
     alt="Una foto de un perro"
     srcset="dog-500.png 500w,
             dog-800.png 800w,
             dog-1000.png 1000w,
             dog-1400.png 1400w">
```

En `srcset` se utiliza la unidad `w` (del inglés *width*) para indicar el ancho de cada imagen.

Cuando se utiliza `srcset` con descriptores `w`, también debe utilizarse el atributo `sizes`:

```html
<img src="dog.png"
     alt="Una foto de un perro"
     sizes="(max-width: 500px) 100vw, (max-width: 900px) 50vw, 800px"
     srcset="dog-500.png 500w,
             dog-800.png 800w,
             dog-1000.png 1000w,
             dog-1400.png 1400w">
```

En este ejemplo, la expresión `(max-width: 500px) 100vw, (max-width: 900px) 50vw, 800px` describe el tamaño que ocupará la imagen según el ancho de la ventana del navegador.

Si la ventana mide menos de `500px`, la imagen ocupará el `100%` del ancho de la ventana (`100vw`).

Si la ventana mide menos de `900px`, pero más de `500px`, la imagen ocupará el `50%` del ancho de la ventana (`50vw`).

En pantallas más grandes, la imagen tendrá un ancho fijo de `800px`.

La unidad `vw` (del inglés *viewport width*) representa el `1%` del ancho de la ventana del navegador. Por ejemplo, `100vw` equivale al `100%` de dicho ancho. Existe también la unidad `vh` (*viewport height*), que representa el `1%` de la altura de la ventana.

Un sitio útil para generar automáticamente las imágenes necesarias para `srcset` es <https://responsivebreakpoints.com/>.

## La etiqueta `picture`

HTML también proporciona la etiqueta `picture`, que cumple un propósito similar al de `srcset`, aunque ofrece un mayor control sobre qué imagen utilizar en cada situación.

Puede utilizar `picture` cuando, en lugar de mostrar una versión más pequeña de una imagen, necesite cambiar completamente el archivo o servir un formato distinto.

Un caso de uso muy común es servir imágenes en formato WebP y proporcionar un formato alternativo para navegadores que no lo soporten. En el siguiente ejemplo, los navegadores compatibles utilizarán la imagen WebP y, en caso contrario, cargarán la versión JPG:

```html
<picture>
  <source type="image/webp" srcset="image.webp">
  <img src="image.jpg" alt="Una imagen">
</picture>
```

> La etiqueta `source` permite definir uno o más recursos alternativos. La etiqueta `img` actúa como recurso de respaldo para navegadores que no admiten `picture`.

La etiqueta `source` también admite el atributo `media`, que permite utilizar consultas de medios (*media queries*) para seleccionar la imagen más adecuada.

El siguiente ejemplo funciona de forma similar al uso de `srcset`:

```html
<picture>
  <source media="(min-width: 500px)" srcset="dog-500.png" sizes="100vw">
  <source media="(min-width: 800px)" srcset="dog-800.png" sizes="100vw">
  <source media="(min-width: 1000px)" srcset="dog-1000.png" sizes="800px">
  <source media="(min-width: 1400px)" srcset="dog-1400.png" sizes="800px">
  <img src="dog.png" alt="Una imagen de un perro">
</picture>
```

Aunque el funcionamiento es similar al de `srcset`, el elemento `picture` ofrece mayor flexibilidad, a costa de requerir algo más de código.

Se trata de una característica ampliamente soportada por los navegadores modernos. Las principales excepciones son Internet Explorer y Opera Mini.