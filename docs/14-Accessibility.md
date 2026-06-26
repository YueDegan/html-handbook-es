# Accesibilidad

Es importante que diseñemos nuestro HTML con la accesibilidad en mente.

Tener un HTML accesible significa que las personas con discapacidad puedan usar su página. Existen personas completa o parcialmente invidentes, personas con pérdida auditiva y una gran variedad de otras discapacidades.

Desafortunadamente, no suele dársele a este aspecto la importancia que requiere, ya que no es tan llamativo como otros temas.

¿Qué pasaría si una persona que no puede *ver* su página quisiera consumir su contenido? En primer lugar, ¿cómo lo hace? No puede usar el ratón; utiliza una herramienta llamada **lector de pantalla**. No tiene por qué imaginárselo cuando puede probarla. Google ofrece la extensión gratuita para Chrome llamada [ChromeVox](https://chrome.google.com/webstore/detail/chromevox/kgejglhpjiefppelpmljglcjbhoiplfn/). La accesibilidad también implica permitir que estas herramientas puedan seleccionar los elementos y navegar por las páginas correctamente.

Las páginas y aplicaciones web no siempre son construidas con la accesibilidad como una de sus principales prioridades y, aunque tal vez la versión 1 no contemple este enfoque, puede hacerse accesible en una iteración futura. Cuanto antes se haga, mejor, pero nunca es demasiado tarde.

Es importante tener esto siempre presente, especialmente cuando se trata de contenido de interés público, como las páginas web de gobiernos u otras organizaciones públicas.

¿Qué significa hacer una página HTML accesible? Permítame ilustrarle los aspectos principales que debe tener en cuenta.

> **Nota:** hay muchos otros aspectos relacionados con la accesibilidad que pertenecen a CSS, como los colores, el contraste y la tipografía. También existen temas específicos, como [cómo hacer accesibles las imágenes SVG](https://css-tricks.com/accessible-svgs/). No hablaremos de ello en este libro.

## Uso de HTML semántico

El HTML semántico es fundamental y es una de las principales responsabilidades al crear una página. Veamos algunos ejemplos comunes.

Es importante utilizar una estructura correcta para los encabezados. La etiqueta más importante es `h1`; las siguientes (`h2`, `h3`, etc.) representan niveles inferiores de jerarquía. Todos los encabezados del mismo nivel deberían representar el mismo nivel de importancia (piense en ello como la estructura de un árbol):

```
h1
	h2
		h3
	h2
	h2
		h3
			h4
```

Utilice `strong` y `em` en lugar de `b` e `i`, respectivamente. Aunque tienen el mismo aspecto visual por defecto, `strong` y `em` aportan significado semántico, mientras que `b` e `i` son elementos principalmente de presentación.

Las listas también son parte importante de la accesibilidad. Un lector de pantalla puede detectar una lista y ofrecer un resumen, permitiendo luego que el usuario decida si desea recorrerla por completo.

Una tabla debería tener una etiqueta `caption` que describa su contenido:

```html
<table>
  <caption>Edad de los perros</caption>
  <tr>
    <th>Perro</th>
    <th>Edad</th>
  </tr>
  <tr>
    <td>Roger</td>
    <td>7</td>
  </tr>
</table>
```

## Use el atributo `alt` para las imágenes

Todas las imágenes deben tener un atributo `alt` que describa su contenido. No solo es una buena práctica, sino que además es un requisito del estándar HTML.

```html
<img src="dog.png" alt="Una foto de mi perro">
```

También ayuda al SEO, por lo que existe otro incentivo para utilizarlo.

## Use el atributo `role`

El atributo `role` permite asignar roles específicos a los distintos elementos de una página.

Existen muchos roles diferentes, todos definidos en inglés, por lo que puede resultar útil consultar un diccionario o la documentación cuando sea necesario.

Son numerosos y, para consultar la referencia completa de cada uno, puede visitar este [enlace de MDN](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles). Sin embargo, no es necesario asignar un rol a todos los elementos de la página. Los lectores de pantalla suelen inferirlo a partir de la etiqueta HTML utilizada. Por ejemplo, no necesita agregar este atributo a etiquetas como `nav`, `button` o `form`.

Tomemos como ejemplo la etiqueta `nav`. Puede usarla para definir la navegación de una página de la siguiente manera:

```html
<nav>
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/blog">Blog</a></li>
  </ul>
</nav>
```

Si estuviera *forzado* a usar una etiqueta `div` en lugar de `nav`, entonces sí debería usar el rol `navigation`:

```html
<div role="navigation">
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/blog">Blog</a></li>
  </ul>
</div>
```

En otras palabras, `role` se utiliza para aportar significado semántico cuando la etiqueta HTML empleada no lo proporciona.

## Use el atributo `tabindex`

Este atributo permite modificar el orden en el que la tecla Tab selecciona los elementos interactivos de una página. Por defecto, los enlaces y los controles de formulario ya forman parte del orden de tabulación, por lo que normalmente no es necesario agregarles `tabindex`.

Agregar `tabindex="0"` a un elemento hace que pueda recibir el foco mediante la tecla Tab:

```html
<div tabindex="0">
...
</div>
```

Por otra parte, usar `tabindex="-1"` elimina el elemento del orden de tabulación, aunque seguirá pudiendo recibir el foco mediante JavaScript.

## Use los atributos `aria`

ARIA es un acrónimo de *Accessible Rich Internet Applications* y define atributos que añaden información semántica a los elementos.

### `aria-label`

Este atributo se utiliza para agregar una descripción textual a un elemento.

Ejemplo:

```html
<p aria-label="Descripción de un producto">...</p>
```

### `aria-labelledby`

Este atributo establece una relación entre el elemento actual y el elemento que actúa como su etiqueta.

Si entiende cómo un elemento `input` puede asociarse con un elemento `label`, puede pensar en `aria-labelledby` de forma similar.

Se indica el identificador (`id`) del elemento que describe al elemento actual.

Ejemplo:

```html
<h3 id="descripcion">Descripción del producto</h3>

<p aria-labelledby="descripcion">
...
</p>
```

### `aria-describedby`

Este atributo permite asociar un elemento con otro que proporciona una descripción adicional.

Ejemplo:

```html
<button aria-describedby="pADescripcion">Pague ahora</button>

<div id="pADescripcion">¡Hacer clic en el botón lo enviará a nuestro formulario!</div>
```

### Use `aria-hidden` para ocultar contenido

El atributo `aria-hidden="true"` indica a los lectores de pantalla que deben ignorar ese elemento.

## Dónde aprender más

Esta es solo una introducción al tema. Para profundizar, recomiendo estos recursos (en inglés):

- [W3C Web Content Accessibility Guidelines (WCAG)](https://www.w3.org/TR/WCAG20/)
- [WebAIM](https://webaim.org/)
- [Google Developers: Accessibility](https://developers.google.com/web/fundamentals/accessibility/)