# Etiquetas que interactúan con el texto

## La etiqueta `p`

Define un párrafo de texto.

```html
<p>Algún texto</p>
```

Es un elemento en bloque.

Dentro de él, podemos agregar cualquier elemento en línea que queramos, como `span` o `a`.

No podemos agregar elementos de bloque. Tampoco podemos crear un elemento `p` dentro de otro.

Por defecto, los navegadores dan estilo a los párrafos con un margen arriba y abajo. Es de `16px` en Chrome, pero el valor exacto puede variar entre navegadores.

Esto hace que dos párrafos consecutivos estén espaciados entre sí, replicando lo que esperaríamos de un "párrafo" en medios como un periódico.

## La etiqueta `span`

Es una etiqueta en línea que puede usarse para crear una sección dentro de un párrafo para que pueda ser modificada con CSS:

```html
<p>Una parte del texto <span>y aquí otra</span></p>
```

## La etiqueta `br`

Esta etiqueta representa un salto de línea. Es un elemento en línea y no necesita etiqueta de cierre.

La usamos para crear saltos de línea dentro de una etiqueta `p`, sin crear un nuevo párrafo.

Y, a diferencia de un nuevo párrafo, no genera espaciado adicional.

```html
<p>Algo de texto<br>Una nueva línea</p>
```

## Etiquetas de encabezado

HTML nos provee 6 etiquetas de encabezado. De la más importante a la menos importante, tenemos `h1`, `h2`, `h3`, `h4`, `h5`, `h6`.

Típicamente, una página tendrá un elemento `h1`, que será el título de la página. Luego puede tener uno o más elementos `h2`, dependiendo del contenido.

Los encabezados, especialmente durante la organización del contenido, son esenciales para el SEO, donde los motores de búsqueda los utilizan de diferentes maneras.

El navegador mostrará por defecto la etiqueta `h1` con el tamaño de texto más grande, reduciéndolo a medida que el número asociado a `h` aumenta:

![](6-Tags-that-interact-with-text/Screen%20Shot%202019-06-11%20at%2019.46.57.png)

Todos los encabezados son elementos en bloque. No pueden contener otros elementos, solo texto.

## La etiqueta `strong`

Esta etiqueta se usa para marcar el texto que contiene como *importante*. Es importante notar esto porque no es una ayuda visual, sino semántica, cuya interpretación dependerá del medio utilizado.

Los navegadores, por defecto, muestran el texto en **negrita**.

## La etiqueta `em`

Esta etiqueta se usa para dar *énfasis* al texto que contiene. Al igual que `strong`, no es una ayuda visual, sino semántica.

Los navegadores, por defecto, muestran el texto en **cursiva**.

## Citas

La etiqueta HTML `blockquote` es útil para insertar citas en el texto. Es una etiqueta en bloque.

Por defecto, los navegadores aplican un margen a un elemento `blockquote`. Chrome aplica un margen de 40px a los lados y de 10px arriba y abajo.

La etiqueta HTML `q` también se usa para citas, pero en línea.

## Línea horizontal

No está realmente basada en texto, pero la etiqueta `hr` suele usarse dentro de una página para agregar una línea horizontal.

Es útil para separar secciones de una página.

## Bloques de código

La etiqueta `code` es especialmente útil para mostrar código, debido a la fuente especial que aplica al texto que contiene.

Eso suele ser lo único que hacen los navegadores con el texto. Este es el CSS aplicado por Chrome:

```css
code {
    font-family: monospace;
}
```

Esta etiqueta suele usarse dentro de una etiqueta `pre`, ya que el elemento `code` ignora los espacios y los saltos de línea, de forma similar a la etiqueta `p`.

Chrome aplica el siguiente estilo a la etiqueta `pre`:

```css
pre {
    display: block;
    font-family: monospace;
    white-space: pre;
    margin: 1em 0px;
}
```

Esto evita que el espacio en blanco se colapse, convirtiéndolo en un elemento en bloque.

## Listas

Tenemos 3 tipos de listas:

- listas sin ordenar
- listas ordenadas
- listas de definiciones

Las listas sin ordenar se crean usando la etiqueta `ul`. Cada elemento de la lista se crea con la etiqueta `li`:

```html
<ul>
	<li>Primero</li>
	<li>Segundo</li>
</ul>
```

Las listas ordenadas son similares, solo que usan la etiqueta `ol`:

```html
<ol>
	<li>Primero</li>
	<li>Segundo</li>
</ol>
```

La diferencia entre ambas es que las listas ordenadas muestran un número antes de cada elemento:

![](6-Tags-that-interact-with-text/Screen%20Shot%202019-06-12%20at%2009.35.05.png)

Las listas de definición son un poco diferentes. Están compuestas por un término y su descripción:

```html
<dl>
	<dt>Flavio</dt>
	<dd>El nombre</dd>
	<dt>Copes</dt>
	<dd>El apellido</dd>
</dl>
```

Típicamente se muestran de la siguiente forma en los navegadores:

![](6-Tags-that-interact-with-text/Screen%20Shot%202019-06-12%20at%2009.45.21.png)

Debo admitir que no se usan tanto en el día a día como las dos anteriores, pero pueden ser útiles en algunas ocasiones.

## Otras etiquetas de texto

Hay otro conjunto de etiquetas con propósitos de presentación:

- la etiqueta `mark`
- la etiqueta `ins`
- la etiqueta `del`
- la etiqueta `sup`
- la etiqueta `sub`
- la etiqueta `small`
- la etiqueta `i`
- la etiqueta `b`

Este es un ejemplo de la visualización aplicada por los navegadores:

![](6-Tags-that-interact-with-text/Screen%20Shot%202019-06-12%20at%2008.43.55.png)

Aquí puede que surja la pregunta: ¿en qué se diferencia `b` de `strong`? ¿Y cómo se diferencia `i` de `em`?

La diferencia radica en el significado semántico. Aunque `b` e `i` son instrucciones directas al navegador para aplicar un estilo específico al texto, `strong` y `em` le dan un significado especial, y queda en manos del navegador el estilo que les otorgue. Casualmente, por defecto es el mismo estilo que `b` e `i`, pero puede cambiarse mediante CSS.

Todavía quedan algunas otras etiquetas relacionadas con el texto por explicar, pero son muy poco usadas.