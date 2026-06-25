# La etiqueta `body`

Después de cerrar la etiqueta `head`, solo podemos tener una etiqueta más en un documento HTML: el elemento `body`.

```html
<!DOCTYPE html>
<html>
	<head>
		...
	</head>
	<body>
		...
	</body>
</html>
```

Al igual que las etiquetas `head` y `html`, solo podemos tener una etiqueta `body` en una página.

Dentro de la etiqueta `body` tenemos todas las etiquetas que definen el contenido de la página.

Técnicamente, las etiquetas de apertura y cierre son opcionales, pero considero que es una buena práctica incluirlas por cuestiones de claridad.

En los próximos capítulos veremos la variedad de etiquetas que se pueden usar dentro del cuerpo de la página.

Pero antes debemos presentar la diferencia entre los elementos de bloque y los elementos en línea.

## Bloques o líneas

Los elementos visuales definidos en el cuerpo de la página pueden clasificarse, por lo general, en dos categorías:

- elementos de bloque (`p`, `div`, listas y sus elementos, ...)
- elementos en línea (`a`, `span`, `img`, ...)

¿Cuál es la diferencia?

Los elementos de bloque, al posicionarse en la página, no permiten que otros elementos se ubiquen a su lado, ya sea a la derecha o a la izquierda.

Los elementos en línea, por el contrario, pueden aparecer junto a otros elementos en línea.

La diferencia también radica en las propiedades visuales que podemos modificar mediante CSS. Podemos alterar la altura, el ancho, los márgenes internos y externos, así como los bordes de los elementos de bloque, mientras que estas propiedades no se comportan de la misma forma en los elementos en línea.

> Nótese que CSS permite cambiar el comportamiento por defecto de los elementos, haciendo que una etiqueta `p` se comporte como un elemento en línea o que un elemento `span` se comporte como uno de bloque.

Otra diferencia es que los elementos en línea pueden estar dentro de elementos de bloque, pero no al revés.

Algunos elementos de bloque pueden contener otros elementos de bloque, pero depende de cada caso. La etiqueta `p`, por ejemplo, no lo permite.