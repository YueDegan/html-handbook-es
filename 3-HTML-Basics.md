# Bases de HTML

HTML es el lenguaje de marcado que usamos para estructurar el contenido que consumimos en internet.

HTML se sirve al navegador de diferentes maneras.

- Puede ser generado por una aplicación del servidor que lo construya dependiendo de la petición o de los datos de la sesión, como por ejemplo Rails, Laravel o Django.
- Puede ser generado por una aplicación de JavaScript del lado del cliente que genere HTML durante su ejecución.
- De manera más simple, puede ser almacenado en un archivo y servido al navegador por medio de un servidor web.

Vayamos a este último caso. Aunque, en la práctica, posiblemente sea la forma menos popular de generar HTML, sigue siendo esencial conocer al menos sus bloques más básicos.

Por convención, un archivo HTML se guarda con la extensión `.html` o `.htm`.

Dentro de este archivo organizamos el contenido usando **etiquetas** (o *tags*, en inglés).

Las etiquetas rodean el contenido, y cada una le da un significado especial al texto que contiene.

Hagamos algunos ejemplos.

Este fragmento de HTML crea un párrafo usando la etiqueta `p`:

```html
<p>Un párrafo de texto</p>
```

Este otro fragmento crea una lista de elementos usando la etiqueta `ul`, que significa *lista sin ordenar* (del inglés *unordered list*), y las etiquetas `li`, que significan *elemento de lista* (*list item*, en inglés):

```html
<ul>
  <li>Primer elemento</li>
  <li>Segundo elemento</li>
  <li>Tercer elemento</li>
</ul>
```

Cuando una página HTML es interpretada por el navegador, las etiquetas son procesadas y los elementos se muestran de acuerdo con las reglas que definen su apariencia visual.

Algunas de estas reglas están establecidas de forma predeterminada, como la manera en que se muestra una lista o cómo un enlace aparece subrayado y en color azul.

Otras pueden ser definidas mediante hojas de estilo en cascada, conocidas comúnmente como CSS.

HTML no es un lenguaje de presentación. No se preocupa por cómo se *ven* las cosas, sino por lo que *significan*.

Corresponde al navegador determinar cómo se ven los elementos siguiendo las reglas definidas por quien crea la página mediante CSS.

Sin embargo, esos dos ejemplos eran fragmentos tomados fuera del contexto de una página real.

### Estructura de una página HTML

Hagamos un ejemplo de una página HTML real.

Todo comienza con la declaración del tipo de documento (conocida como *doctype*), una manera de decirle al navegador que lo que está "viendo" es una página HTML, así como la versión que se está utilizando.

El HTML moderno usa esta declaración:

```html
<!DOCTYPE html>
```

Luego tenemos el elemento `html`, que posee una etiqueta de apertura y una de cierre:

```html
<!DOCTYPE html>
<html>
...
</html>
```

La mayoría de las etiquetas vienen en pares: una etiqueta de apertura y otra de cierre. La etiqueta de cierre se escribe casi de la misma manera que la de apertura, pero con un `/`:

```html
<etiqueta>contenido</etiqueta>
```

Hay algunas etiquetas que no requieren una etiqueta de cierre, ya que **no contienen** ningún contenido.

La etiqueta de apertura `html` se utiliza al principio del documento, después de la declaración del tipo de documento.

La etiqueta de cierre de `html` es lo último presente en un documento HTML.

Dentro del elemento `html` tenemos dos elementos: `head` y `body`:

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

Dentro de `head` tendremos etiquetas esenciales para la creación de una página web, como el título, los metadatos, el CSS interno o externo y el código JavaScript. La mayoría de estos elementos no aparecen directamente en la página, sino que ayudan al navegador (o a los motores de búsqueda) a mostrarla correctamente.

Dentro de `body` tendremos el contenido de la página: las **cosas visibles**.

### Etiquetas o elementos

Mencioné etiquetas y elementos. ¿Cuál es la diferencia?

Los elementos tienen una etiqueta de apertura y una de cierre. En este ejemplo usamos las etiquetas de apertura y cierre `p` para crear un elemento `p`:

```html
<p>Un párrafo de texto</p>
```

Así, un elemento constituye el *conjunto completo*:

- una etiqueta de apertura;
- el contenido (y, posiblemente, otros elementos);
- una etiqueta de cierre.

Si un elemento no tiene una etiqueta de cierre, está compuesto únicamente por la etiqueta de apertura y, por ello, no puede contener texto.

Explicado esto, puedo usar ambos términos de manera intercambiable, a menos que se mencione explícitamente una etiqueta de apertura o de cierre.

### Atributos

La etiqueta de apertura de un elemento puede contener fragmentos especiales de información llamados **atributos**.

Los atributos siguen la sintaxis `atributo="valor"`:

```html
<p class="una-clase">Un párrafo de texto</p>
```

> También pueden usarse comillas simples, pero es una buena práctica utilizar comillas dobles.

Podemos tener varios atributos:

```html
<p class="una-clase" id="un-id">Un párrafo de texto</p>
```

Algunos atributos son booleanos, lo que significa que basta con escribir el nombre del atributo:

```html
<script defer src="archivo.js"></script>
```

Los atributos `class` e `id` son de los que más encontrará.

Tienen un significado especial y son útiles tanto en CSS como en JavaScript.

La diferencia entre ambos es que un `id` debe ser único dentro de una página web; no puede repetirse.

Las clases, por otra parte, pueden aparecer múltiples veces y en múltiples elementos.

Además, un `id` solo puede tener un valor. `class`, por su parte, puede contener varios valores separados por espacios:

```html
<p class="una-clase otra-clase">Un párrafo de texto</p>
```

Es común usar guiones (`-`) para separar palabras en un nombre de clase, aunque no es obligatorio.

Estos son solo dos de los muchos atributos que puede usar. Algunos solo pueden utilizarse en determinadas etiquetas, ya que son altamente especializados.

Otros atributos son de uso general. Ya vimos `id` y `class`, pero también existe `style`, que puede utilizarse para agregar CSS directamente a un elemento (aunque es una práctica poco recomendable).

### ¿Mayúsculas o minúsculas?

En HTML es irrelevante usar mayúsculas o minúsculas en los nombres de las etiquetas. Estas pueden escribirse completamente en mayúsculas o en minúsculas. Antiguamente era común usar mayúsculas, pero hoy en día lo habitual es escribirlas en minúsculas.

Usualmente escribiría:

```html
<p>Un párrafo de texto</p>
```

y no:

```html
<P>Un párrafo de texto</P>
```

### Espaciado

Un detalle importante: en HTML el espaciado, por lo general, no es relevante. Durante la interpretación del documento, los espacios en blanco consecutivos se colapsan.

Para el navegador,

```html
<p>Un párrafo de texto</p>
```

es lo mismo que:

```html
<p>        Un párrafo de texto</p>
```

y también que:

```html
<p>Un párrafo

de
           texto</p>
```

Le aconsejaría usar una sintaxis que le permita organizar visualmente los elementos para facilitar su lectura, aunque es libre de utilizar el estilo que prefiera.

Yo prefiero:

```html
<p>Un párrafo de texto</p>
```

o:

```html
<p>
	Un párrafo de texto
</p>
```

Las etiquetas contenidas dentro de otras deberían indentarse con dos o cuatro espacios (o con tabulaciones, según su preferencia):

```html
<body>
	<p>
		Un párrafo de texto
	</p>
	<ul>
		<li>Un elemento de lista</li>
	</ul>
</body>
```

> **Nota:** Esta característica del espaciado implica que, si desea agregar espacios visibles, hacerlo únicamente con espacios puede resultar complicado. Lo recomendable es usar CSS cuando sea necesario modificar la separación entre elementos.

> **Nota:** En casos especiales puede usar la entidad HTML `&nbsp;` (*non-breaking space* o espacio de no separación), pero hablaré de ella más adelante. Sin embargo, considero que no debería abusarse de su uso. Es preferible utilizar CSS para controlar la presentación visual.