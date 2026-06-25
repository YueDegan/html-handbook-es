# La etiqueta `head`

Esta etiqueta contiene otras etiquetas especiales que definen las propiedades del documento.

Siempre se escribe antes de la etiqueta `body`, justo después de la etiqueta de apertura `html`:

```html
<!DOCTYPE html>
<html>
	<head>
		...
	</head>
	...
</html>
```

Nunca usamos atributos en esta etiqueta. Tampoco escribimos contenido en ella, ya que es solo un contenedor para otras etiquetas.

Algunas de ellas son las siguientes, dependiendo de lo que se necesite:

- `title`
- `script`
- `noscript`
- `link`
- `style`
- `base`
- `meta`

### La etiqueta `title`

Esta etiqueta determina el título de la página. Este se muestra en el navegador y es especialmente importante, ya que forma parte esencial de la optimización para motores de búsqueda (SEO, por sus siglas en inglés).

### La etiqueta `script`

Esta etiqueta se usa para agregar JavaScript a la página.

Puede agregarlo dentro del mismo documento, con una etiqueta de apertura, el código y una etiqueta de cierre:

```html
<script>
..código JS
</script>
```

O, alternativamente, puede cargar un archivo JavaScript externo usando el atributo `src`:

```html
<script src="archivo.js"></script>
```

> El atributo `type`, por defecto, está configurado como `text/javascript`, por lo que es completamente opcional.

Hay un detalle bastante importante respecto a esta etiqueta.

Si existe, suele colocarse al final de la página, justo antes de la etiqueta de cierre `</body>`. ¿Por qué? Por cuestiones de rendimiento.

Al cargar código JavaScript (o scripts), el navegador bloquea, por defecto, la visualización de la página hasta que el script haya sido interpretado y cargado.

Al colocarlo al final de la página, se carga y ejecuta después de que esta haya sido interpretada y cargada, lo que brinda una mejor experiencia al usuario que si estuviera en la etiqueta `head`.

En mi opinión, hoy en día esta práctica ya no es recomendable. No hay problema en dejar las etiquetas `script` dentro de `head`.

En el JavaScript moderno tenemos una alternativa mejor que colocar los scripts al final: el atributo `defer`. Este es un ejemplo que carga un `archivo.js` relativo a la dirección actual:

```html
<script defer src="archivo.js"></script>
```

Con esto, se obtiene un escenario que permite cargar tanto la página como el JavaScript de forma más eficiente.

### La etiqueta `noscript`

Esta etiqueta se usa para detectar si los scripts están deshabilitados en el navegador.

> **Nota:** Los usuarios pueden elegir deshabilitar los scripts de JavaScript en la configuración del navegador, así como también puede ocurrir que el navegador no los soporte por defecto.

Se usa de manera distinta dependiendo del lugar en el que se coloque, ya sea dentro de la etiqueta `head` o de la etiqueta `body`.

Ya que estamos hablando de esta etiqueta, presentaré su uso.

En este caso, la etiqueta `noscript` solo puede contener las siguientes etiquetas:

- `link`
- `style`
- `meta`

para alterar los recursos servidos por la página, en caso de que los scripts estén deshabilitados.

En este ejemplo, se establece un elemento con la clase `no-script-alert` para que se muestre si los scripts están desactivados, ya que, por defecto, tiene la propiedad CSS `display: none`:

```html
<!DOCTYPE html>
<html>
	<head>
		...
		<noscript>
			<style>
				.no-script-alert {
					display: block;
				}
			</style>
		</noscript>

		...
	</head>
	...
</html>
```

> Por otra parte, si se coloca dentro de la etiqueta `body`, puede contener párrafos u otros elementos para ser mostrados en la interfaz de usuario.

### La etiqueta `link`

Se usa para establecer relaciones entre un documento y otros recursos.

Se usa principalmente para enlazar y cargar un archivo CSS externo.

Este elemento no tiene etiqueta de cierre.

Uso:

```html
<!DOCTYPE html>
<html>
	<head>
		...
		<link href="archivo.css" rel="stylesheet">
		...
	</head>
	...
</html>
```

El atributo `media` permite cargar diferentes hojas de estilo dependiendo de las capacidades del dispositivo:

```html
<link href="file.css" media="screen" rel="stylesheet">
<link href="print.css" media="print" rel="stylesheet">
```

También se pueden enlazar otros recursos además de hojas de estilo.

Por ejemplo, podemos enlazar una fuente RSS usando:

```html
<link rel="alternate" type="application/rss+xml" href="/index.xml">
```

O podemos enlazar un favicon usando:

```html
<link rel="apple-touch-icon" sizes="180x180" href="/assets/apple-touch-icon.png">

<link rel="icon" type="image/png" sizes="32x32" href="/assets/favicon-32x32.png">

<link rel="icon" type="image/png" sizes="16x16" href="/assets/favicon-16x16.png">
```

Esta etiqueta **fue** usada por Google para contenido multipágina, con el fin de indicar la página anterior y la siguiente mediante `rel="prev"` y `rel="next"`. Hasta el momento de la escritura de este libro (2019), [Google anunció que ya no utiliza estas etiquetas](https://twitter.com/googlewmc/status/1108726443251519489), ya que puede determinar correctamente la estructura del sitio sin ellas.

### La etiqueta `style`

Puede usarse para agregar estilos al documento, en lugar de cargar una hoja de estilos externa.

Uso:

```html
<style>
.algun-css {}
</style>
```

Al igual que con la etiqueta `link`, puede usar el atributo `media` para especificar dónde se utilizará ese CSS:

```html
<style media="print">
.some-css {}
</style>
```

### La etiqueta `base`

Se usa para establecer una dirección base para todas las direcciones relativas contenidas en la página.

```html
<!DOCTYPE html>
<html>
	<head>
		...
		<base href="https://github.com/zetta102">
		...
	</head>
	...
</html>
```

### La etiqueta `meta`

Las etiquetas `meta` cumplen una variedad de tareas importantes, especialmente en lo referente al SEO.

Los elementos `meta` solo tienen una etiqueta de apertura.

La más básica es la etiqueta `meta` de `description`, usada para describir una página:

```html
<meta name="description" content="Una bonita página">
```

Esto **puede** ser usado por Google para generar la descripción de la página en los resultados de búsqueda, en caso de que la considere mejor que el contenido de la propia página (no me pregunten cómo).

La etiqueta `meta` de `charset` se usa para establecer la codificación de caracteres de la página. En la mayoría de los casos, suele ser `utf-8`:

```html
<meta charset="utf-8">
```

La etiqueta `meta` de `robots` indica al motor de búsqueda si puede o no indexar una página (es decir, mostrarla en los resultados de búsqueda):

```html
<meta name="robots" content="noindex">
```

También permite indicar si debe seguir los enlaces o no:

```html
<meta name="robots" content="nofollow">
```

> También puede establecerse en enlaces individuales. Esta es una forma de configurarlo de manera global.

Ambas opciones pueden combinarse:

```html
<meta name="robots" content="noindex, nofollow">
```

El comportamiento por defecto es `index, follow`.

También puede usar otras directivas, como `nosnippet`, `noarchive`, `noimageindex`, entre otras.

También puede dirigirse específicamente a Google, en lugar de a todos los motores de búsqueda:

```html
<meta name="googlebot" content="noindex, nofollow">
```

Otros motores de búsqueda también pueden tener sus propias etiquetas `meta`.

Hablando de ello, podemos pedirle a Google que deshabilite algunas características. Esto evita, por ejemplo, que aparezca la funcionalidad de traducción en los resultados de búsqueda:

```html
<meta name="google" content="notranslate">
```

La etiqueta `meta` `viewport` se usa para indicarle al navegador que establezca el ancho de la página en función del ancho del dispositivo.

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Otra etiqueta `meta` bastante popular es `http-equiv="refresh"`. En este caso, indica al navegador que redirija a otra página después de esperar tres segundos:

```html
<meta http-equiv="refresh" content="3;url=http://otra-pagina.com">
```

Usar `0` hará que la redirección ocurra tan rápido como sea posible.

Vale aclarar que esta no es una referencia completa; existen muchas otras etiquetas `meta` menos utilizadas.

Después de este documento, podremos profundizar en el cuerpo del mismo.