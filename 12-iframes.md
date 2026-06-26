# Iframes

La etiqueta `iframe` nos permite agregar contenido de otro origen (otras páginas) a nuestra página web.

A nivel técnico, un iframe crea el contenido de forma anidada. Esto significa que el iframe no interfiere con la página original y viceversa. JavaScript y/o CSS no "se filtran" desde o hacia los iframes.

Muchos sitios usan iframes para ejecutar varios procesos. Puede que conozca CodePen, Glitch u otros sitios que le permiten escribir código en una parte de la página y luego ver el resultado en otra. Eso es un iframe.

Puede crear uno de la siguiente manera:

```html
<iframe src="page.html"></iframe>
```

También puede hacer referencia a una URL absoluta:

```html
<iframe src="https://site.com/page.html"></iframe>
```

También puede establecer parámetros de altura y anchura. En caso de que no lo haga, el iframe usará los valores por defecto: una caja de 300 × 150 píxeles:

```html
<iframe src="page.html" width="800" height="400"></iframe>
```

## Srcdoc

El atributo `srcdoc` le permite especificar código HTML para mostrar. Es una alternativa a `src`, pero es más reciente y no está soportado por Edge 18 ni versiones anteriores, así como tampoco por Internet Explorer:

```html
<iframe srcdoc="<p>My dog is a good dog</p>"></iframe>
```

## Sandbox

El atributo `sandbox` permite limitar las operaciones permitidas dentro de los iframes.

Si lo omitimos, todo estará permitido:

```html
<iframe src="page.html"></iframe>
```

Si lo establecemos en `""`, nada estará permitido:

```html
<iframe src="page.html" sandbox=""></iframe>
```

Podemos seleccionar las acciones permitidas añadiendo opciones al atributo `sandbox`. Puede habilitar múltiples acciones separándolas con espacios. Esta es una lista incompleta de las opciones disponibles:

- `allow-forms`: permite enviar formularios.
- `allow-modals`: permite abrir ventanas modales, incluyendo llamadas a `alert()` desde JavaScript.
- `allow-orientation-lock`: permite bloquear la orientación de la pantalla.
- `allow-popups`: permite abrir ventanas emergentes mediante `window.open()` y enlaces con `target="_blank"`.
- `allow-same-origin`: trata el recurso cargado como si perteneciera al mismo origen.
- `allow-scripts`: permite ejecutar scripts dentro del iframe, pero no abrir ventanas emergentes.
- `allow-top-navigation`: permite al iframe acceder al nivel superior de navegación.

## Allow

Actualmente es un atributo experimental y solo está soportado por navegadores basados en Chromium. Representa el futuro del intercambio de permisos entre la ventana principal y el iframe.

Es similar al atributo `sandbox`, pero permite conceder permisos más específicos, entre ellos:

- `accelerometer`, que da acceso a la API del acelerómetro.
- `ambient-light-sensor`, que da acceso a la API `AmbientLightSensor`.
- `autoplay`, que permite la reproducción automática de archivos de audio y video.
- `camera`, que da acceso a la cámara del dispositivo mediante la API `getUserMedia`.
- `display-capture`, que permite acceder al contenido de la pantalla mediante la API `getDisplayMedia`.
- `fullscreen`, que permite acceder al modo de pantalla completa.
- `geolocation`, que da acceso a la API de geolocalización.
- `gyroscope`, que da acceso a la API del giroscopio.
- `magnetometer`, que da acceso a la API del magnetómetro.
- `microphone`, que da acceso al micrófono del dispositivo mediante la API `getUserMedia`.
- `midi`, que da acceso a la API Web MIDI.
- `payment`, que da acceso a la API de solicitudes de pago.
- `speaker`, que permite la reproducción de audio mediante los altavoces del dispositivo.
- `usb`, que da acceso a la API WebUSB.
- `vibrate`, que da acceso a la API de vibración.
- `vr`, que da acceso a la API WebVR.

## Referrer

Al cargar un iframe, el navegador envía información sobre la página de origen mediante el encabezado HTTP `Referer`.

El atributo `referrerpolicy` permite establecer qué información será enviada al iframe durante la carga. Estos son los valores permitidos:

- `no-referrer-when-downgrade`, que es el valor por defecto, envía la información cuando la página actual se carga mediante HTTPS y el iframe mediante HTTP.
- `no-referrer`, que no envía información en el encabezado.
- `origin`, que envía únicamente el origen (protocolo, dominio y puerto).
- `origin-when-cross-origin`, que envía la URL completa cuando el recurso pertenece al mismo origen y solo el origen cuando pertenece a uno distinto.
- `same-origin`, que envía la información únicamente si el iframe pertenece al mismo origen.
- `strict-origin`, que envía únicamente el origen cuando tanto la página actual como el iframe usan HTTPS. No envía información si el iframe usa HTTP.
- `strict-origin-when-cross-origin`, que envía la URL completa cuando ambos recursos pertenecen al mismo origen; en solicitudes entre distintos orígenes, envía únicamente el origen si ambos usan HTTPS. No envía información si el iframe usa HTTP.
- `unsafe-url`, que envía la URL completa incluso al cargar recursos mediante HTTP desde una página cargada mediante HTTPS.