# Enlaces

Los enlaces se definen usando la etiqueta `a`. El destino del enlace se indica en su atributo `href`.

Ejemplo:

```html
<a href="https://flaviocopes.com">haz click aquí</a>
```

Entre la etiqueta de apertura y la de cierre tendremos el texto del enlace.

El ejemplo anterior es una dirección absoluta. Los enlaces también funcionan con direcciones relativas:

```html
<a href="/test">haz click aquí</a>
```

En este caso, al hacer click en el enlace, el usuario es redirigido a la dirección `/test`, partiendo desde el punto actual.

Tenga cuidado con el carácter `/`. Si se omite, en lugar de comenzar desde la raíz, el navegador simplemente agregará la palabra `test` a la dirección actual.

Por ejemplo, si estoy en la página `https://flaviocopes.com/axios/` y tengo los enlaces `/test` y `test`:

- `/test` me llevará a `https://flaviocopes.com/test`
- `test` me llevará a `https://flaviocopes.com/axios/test`

Las etiquetas de enlace pueden contener otros elementos además de texto. Por ejemplo, imágenes:

```html
<a href="https://flaviocopes.com">
	<img src="test.jpg">
</a>
```

o cualquier otro elemento, excepto otras etiquetas `a`.

Si desea que el enlace se abra en una nueva ventana, puede usar el atributo `target`:

```html
<a href="https://flaviocopes.com" target="_blank">abrir en nueva ventana</a>
```