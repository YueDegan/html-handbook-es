# Etiquetas multimedia: `audio` y `video`

En esta sección quiero mostrarle las etiquetas `audio` y `video`.

## La etiqueta `audio`

Esta etiqueta le permite agregar audio a sus páginas HTML.

Este elemento puede transmitir audio mediante `getUserMedia()` o reproducirlo desde una fuente de audio a la que debe hacer referencia mediante el atributo `src`:

```html
<audio src="file.mp3">
```

Por defecto, el navegador no muestra controles para este elemento, lo que significa que el audio solo se reproducirá si se establece la reproducción automática (explicación al respecto más adelante), y el usuario no podrá detenerlo, cambiar el volumen o desplazarse a una posición específica del audio.

Para mostrar controles, puede agregar el atributo `controls`:

```html
<audio src="file.mp3" controls>
```

Los controles de esta etiqueta pueden tener un aspecto visual personalizado.

Puede especificar el tipo MIME del archivo de audio usando el atributo `type`. Si no se agrega, el navegador intentará determinarlo de forma automática:

```html
<audio src="file.mp3" controls type="audio/mpeg">
```

Por defecto, un archivo de audio no se reproduce automáticamente. Agregue el atributo `autoplay` para habilitar esta funcionalidad:

```html
<audio src="file.mp3" controls autoplay>
```

> Nota: los navegadores móviles no permiten la reproducción automática.

El atributo `loop` reinicia la reproducción desde el inicio. Si no se agrega, la reproducción se detiene al finalizar:

```html
<audio src="file.mp3" controls autoplay loop>
```

También puede reproducir un archivo de audio con el volumen silenciado usando el atributo `muted`:

```html
<audio src="file.mp3" controls autoplay loop muted>
```

Usando JavaScript puede detectar varios eventos que pueden ocurrir en un elemento `audio`, entre los más básicos:

- `play`, cuando el archivo comienza a reproducirse.
- `pause`, cuando la reproducción del archivo se pausa.
- `playing`, cuando la reproducción del archivo continúa.
- `ended`, cuando finaliza la reproducción del archivo.

## La etiqueta `video`

Esta etiqueta le permite agregar video a una página HTML.

Este elemento puede transmitir video mediante `getUserMedia()` o **WebRTC**, o reproducirlo desde una fuente de video a la que debe hacer referencia mediante el atributo `src`:

```html
<video src="file.mp4">
```

Al igual que con los archivos de audio, el navegador no muestra controles por defecto para este elemento, por lo que el usuario no podrá reproducir, pausar, cambiar el volumen o desplazarse a una posición específica del video.

Para mostrar los controles, puede agregar el atributo `controls`:

```html
<video src="file.mp4" controls>
```

Los controles de esta etiqueta pueden tener un aspecto visual personalizado.

Puede especificar el tipo MIME del archivo de video usando el atributo `type`. Si no se agrega, el navegador intentará determinarlo de forma automática:

```html
<video src="file.mp4" controls type="video/mp4">
```

Por defecto, un archivo de video no se reproduce automáticamente. Agregue el atributo `autoplay` para habilitar esta funcionalidad:

```html
<video src="file.mp4" controls autoplay>
```

Algunos navegadores también requieren el atributo `muted` para permitir la reproducción automática. De esta manera, el video se reproducirá automáticamente solo si está silenciado por defecto:

```html
<video src="file.mp4" controls autoplay muted>
```

El atributo `loop` reinicia la reproducción desde el inicio. Si no se agrega, la reproducción se detiene al finalizar:

```html
<video src="file.mp4" controls autoplay loop>
```

También puede definir una imagen para que se muestre por defecto antes de reproducir el video:

```html
<video src="file.mp4" poster="picture.png">
```

Si no está definida, el navegador mostrará el primer cuadro del video apenas esté disponible.

Puede establecer los atributos `width` (anchura) y `height` (altura) para definir el espacio que ocupará el elemento, permitiendo que el navegador reserve dicho espacio y evitando cambios en la interfaz cuando termine de cargarse.

Toman un valor numérico, expresado en píxeles.

Usando JavaScript puede detectar varios eventos que pueden ocurrir en un elemento `video`, entre los más básicos:

- `play`, cuando el archivo comienza a reproducirse.
- `pause`, cuando la reproducción del archivo se pausa.
- `playing`, cuando la reproducción del archivo continúa.
- `ended`, cuando finaliza la reproducción del archivo.