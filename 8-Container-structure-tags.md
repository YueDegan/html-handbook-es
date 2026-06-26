# Etiquetas de contenedor y estructura de página

## Etiquetas de contenedor

HTML provee un conjunto de etiquetas contenedor. Estas etiquetas contienen un conjunto no especificado de otras etiquetas.

Tenemos:

- `article`
- `section`
- `div`

y puede ser difícil entender la diferencia entre ellas.

Veamos cuándo usar cada una.

### `article`

Esta etiqueta identifica una *cosa* que puede ser independiente de otras *cosas* en una página.

Por ejemplo, una lista de posts en la página principal.

O una lista de enlaces.

```html
<div>
	<article>
		<h2>Un post</h2>
		<a ...>Leer más</a>
	</article>
	<article>
		<h2>Otro post</h2>
		<a ...>Leer más</a>
	</article>
</div>
```

El límite no son solo las listas: un artículo puede ser el elemento principal de una página.

```html
<article>
	<h2>Un post</h2>
	<p>Contenido...</p>
</article>
```

Dentro de una etiqueta `article` deberíamos tener un título (`h1`-`h6`) y contenido.

### `section`

Representa una sección de un documento. Cada sección suele tener una etiqueta de encabezado (`h1`-`h6`) y luego el cuerpo de la sección.

Ejemplo:

```html
<section>
	<h2>Una sección de la página</h2>
	<p>...</p>
	<img ...>
</section>
```

Es útil dividir un artículo largo en diferentes **secciones**.

No debería usarse como un elemento contenedor genérico, ya que ese es el trabajo de `div`.

### `div`

`div` es el elemento contenedor genérico:

```html
<div>
	...
</div>
```

Suele agregarse un atributo `class` o `id` a este elemento para poder estilizarlo con CSS.

Usamos `div` en cualquier lugar donde necesitemos un contenedor, pero las etiquetas existentes no se ajusten adecuadamente.

## Etiquetas relacionadas con la página

### `nav`

Esta etiqueta se usa para crear el esqueleto que define la navegación de la página. Dentro de ella suele agregarse una lista `ul` u `ol`:

```html
<nav>
	<ol>
		<li><a href="/">Home</a></li>
		<li><a href="/blog">Blog</a></li>
	</ol>
</nav>
```

### `aside`

La etiqueta `aside` se usa para agregar contenido relacionado con el contenido principal.

Una caja en la que se puede agregar una cita, por ejemplo, o una barra lateral.

Ejemplo:

```html
<div>
  <p>algún texto..</p>
  <aside>
    <p>Una cita..</p>
  </aside>
  <p>otro texto...</p>
</div>
```

Usar `aside` permite señalar que el contenido que contiene no forma parte del flujo principal del documento.

### `header`

La etiqueta `header` representa la introducción (o resumen) de una página. Puede contener una o más etiquetas de encabezado (`h1`-`h6`), un resumen o una imagen.

```html
<article>
  <header>
	  <h1>Título del artículo</h1>
  </header>
  ...
</article>
```

### `main`

La etiqueta `main` representa el contenido principal del documento:

```html
<article>
  ....
  <main>
    <p>....</p>
  </main>
</article>
```

### `footer`

La etiqueta `footer` se usa para definir el pie de un artículo o el pie de una página:

```html
<article>
 ....
  <footer>
    <p>Pie de nota..</p>
  </footer>
</article>
```