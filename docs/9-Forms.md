# Formularios

Los formularios son una forma de interactuar con una página o una aplicación construida con tecnologías web.

Tienen un conjunto de controles y, cuando se envían, ya sea mediante un botón dedicado o por medio de código, el navegador envía la información al servidor.

Por defecto, este envío de información hace que la página se recargue después de enviar los datos, pero este comportamiento puede modificarse con JavaScript. Sin embargo, este libro está dedicado únicamente a HTML.

Un formulario se crea usando la etiqueta `form`:

```html
<form>
	...
</form>
```

Por defecto, los formularios se envían usando el método HTTP `GET`, el cual tiene algunas limitaciones, por lo que normalmente preferirá usar `POST`.

Puede cambiar el método de envío mediante el atributo `method`:

```html
<form method="POST">
	...
</form>
```

El formulario se enviará, ya sea usando `GET` o `POST`, a la misma dirección en la que está alojado.

Así, si el formulario está en `https://flaviocopes.com/contacts`, al presionar el botón de envío hará una petición a esa misma dirección.

Lo que puede provocar que no ocurra nada.

Se necesita algo del lado del servidor para procesar la petición, y normalmente estas solicitudes se gestionan mediante una dirección dedicada.

Puede especificar esa dirección por medio del atributo `action`:

```html
<form action="/new-contact" method="POST">
	...
</form>
```

Esto hará que el navegador envíe los datos del formulario mediante el método `POST` a la dirección `/new-contact` del mismo origen.

Si el origen (es decir, protocolo + dominio + puerto) es `https://flaviocopes.com` (siendo el puerto 80 el usado por defecto), esto significa que los datos del formulario serán enviados a `https://flaviocopes.com/new-contact`.

Hablé de datos, ¿pero cuáles datos?

Los datos son proporcionados por los usuarios mediante un conjunto de controles disponibles en la plataforma web:

- Cajas de texto (de una sola línea)
- Áreas de texto (de varias líneas)
- Listas desplegables (de selección única)
- Botones de opción (o *radio buttons*, de selección única en una lista siempre visible)
- Casillas de verificación (o *checkboxes*, de selección múltiple o ninguna)
- Subida de archivos
- ¡Y mucho más!

Procederé a presentar cada uno de ellos a continuación.

## La etiqueta `input`

Este campo es uno de los elementos de formulario más utilizados. También es un elemento muy versátil, que puede cambiar completamente su comportamiento según el valor de su atributo `type`.

El comportamiento por defecto es el de un campo de texto de una sola línea:

```html
<input>
```

Y eso es equivalente a:

```html
<input type="text">
```

Como ocurre con todos los demás campos que veremos a continuación, debe asignarse un nombre al campo para que su contenido pueda identificarse correctamente cuando el formulario se envíe al servidor:

```html
<input type="text" name="username">
```

El atributo `placeholder` se usa para mostrar un texto en color gris claro dentro del campo cuando está vacío. Es útil para dar una pista al usuario sobre la información que debe introducir:

```html
<input type="text" name="username" placeholder="Su nombre de usuario">
```

### Email

Usar `type="email"` validará la información introducida del lado del cliente (es decir, en el navegador), para comprobar que tenga un formato sintácticamente correcto. Esto no verifica que la dirección de correo exista.

```html
<input type="email" name="email" placeholder="Su correo">
```

### Contraseña

Usar `type="password"` hará que cualquier información introducida se muestre como asteriscos (`*`) o puntos, lo cual resulta útil para campos destinados a contraseñas.

```html
<input type="password" name="password" placeholder="Su contraseña">
```

### Números

Puede tener un campo que únicamente acepte números:

```html
<input type="number" name="edad" placeholder="Su edad">
```

Puede especificar un valor mínimo y máximo mediante los atributos `min` y `max`, respectivamente:

```html
<input type="number" name="edad" placeholder="Su edad" min="18" max="110">
```

El atributo `step` permite establecer los incrementos permitidos entre distintos valores. Por ejemplo, este campo acepta valores entre 10 y 50, en incrementos de 5 unidades:

```html
<input type="number" name="un-numero" min="10" max="50" step="5">
```

### Campo oculto

Los campos pueden estar ocultos para el usuario y, aun así, su información será enviada al servidor:

```html
<input type="hidden" name="campo-oculto" value="algun-valor">
```

Esto se usa para almacenar valores como un token CSRF, útil para la seguridad, la identificación del usuario e incluso para la detección de bots que envían spam mediante técnicas específicas.

También puede usarse para identificar un formulario y la acción que realiza.

### Configurando un valor por defecto

Todos estos tipos aceptan un valor por defecto. Si el usuario no lo modifica, ese será el valor enviado al servidor:

```html
<input type="number" name="edad" value="18">
```

Si usa un `placeholder`, este aparecerá únicamente cuando el campo esté vacío. Si el campo tiene un atributo `value`, será este el que se muestre inicialmente:

```html
<input type="number" name="edad" placeholder="Su edad" value="18">
```

## Envío de formulario

El campo `type="submit"` crea un botón que, al ser presionado, envía el formulario:

```html
<input type="submit">
```

El atributo `value` establece el texto del botón, que por defecto es "Submit":

```html
<input type="submit" value="Haz clic">
```

## Validación de formularios

Los navegadores proporcionan funcionalidades de validación del lado del cliente para los formularios.

Puede marcar campos como obligatorios, asegurarse de que hayan sido completados e imponer un formato determinado para los datos introducidos.

Veamos ambas opciones.

### Establecer campos obligatorios

El atributo `required` ayuda a validar los campos. Si un campo obligatorio está vacío, la validación del lado del cliente falla y el navegador no envía el formulario:

```html
<input type="text" name="nombre-de-usuario" required>
```

### Establecer un formato específico

Describí `type="email"` hace unos párrafos. Este valida automáticamente la dirección de correo electrónico de acuerdo con el formato definido en su especificación.

En el campo `type="number"` mencioné los atributos `min` y `max` para limitar los valores a un intervalo determinado.

Pero puede hacer más.

Puede imponer un formato específico en cualquier campo.

El atributo `pattern` permite establecer una expresión regular (*regular expression*, en inglés) con la que se comparará la información introducida.

Recomiendo leer mi guía sobre expresiones regulares en el siguiente enlace, disponible en inglés.

```html
<input type="text" name="username" pattern="[a-zA-Z]{8}">
```

## Otros campos

### Subida de archivos

Puede subir archivos locales desde su computador y enviarlos al servidor usando un elemento con el atributo `type="file"`:

```html
<input type="file" name="documentos-secretos">
```

También puede adjuntar múltiples archivos:

```html
<input type="file" name="documentos-secretos" multiple>
```

Puede especificar uno o más tipos de archivo permitidos con el atributo `accept`. Este ejemplo acepta imágenes:

```html
<input type="file" name="documentos-secretos" accept="image/*">
```

Puede usar un tipo MIME específico, como `application/json`, o también establecer una o varias extensiones de archivo, como `.pdf`:

```html
<input type="file" name="secret-documents" accept=".jpg, .jpeg, .png">
```

### Botones

Los campos `type="button"` pueden usarse para agregar botones adicionales al formulario que no sean botones de envío:

```html
<input type="button" value="Haz clic">
```

Se usan para ejecutar acciones mediante código JavaScript.

Hay un campo especial que se muestra como un botón y cuya acción consiste en limpiar el formulario completo y restablecer el estado de todos los campos:

```html
<input type="reset">
```

### Botones de opción

Se usan para crear un conjunto de opciones donde, al seleccionar una, las demás quedan deseleccionadas.

El nombre proviene de las antiguas radios de automóvil, que utilizaban este tipo de interfaz.

Se definen mediante un conjunto de elementos `type="radio"`, todos con el mismo atributo `name` y diferentes atributos `value`:

```html
<input type="radio" name="color" value="amarillo">
<input type="radio" name="color" value="rojo">
<input type="radio" name="color" value="azul">
```

Una vez enviado el formulario, el campo `color` tendrá un único valor.

Puede establecer un valor preseleccionado mediante el atributo `checked`. Este solo debe utilizarse una vez por cada grupo de botones de opción.

### Casillas de verificación

Son similares a los botones de opción, pero permiten seleccionar varios valores o ninguno.

Se definen mediante un conjunto de elementos `type="checkbox"`, todos con el mismo atributo `name` y diferentes atributos `value`:

```html
<input type="checkbox" name="color" value="amarillo">
<input type="checkbox" name="color" value="rojo">
<input type="checkbox" name="color" value="azul">
```

Ninguna de estas casillas estará seleccionada por defecto. Puede usar el atributo `checked` para marcar alguna al cargar la página.

Como este campo permite múltiples valores, al enviar el formulario estos serán enviados al servidor como un conjunto de valores.

### Fecha y hora

Tenemos varios campos que aceptan valores de fecha.

El campo `type="date"` permite al usuario introducir una fecha y muestra un selector cuando es necesario:

```html
<input type="date" name="cumpleaños">
```

El campo `type="time"` permite al usuario introducir una hora y muestra un selector cuando es necesario:

```html
<input type="time" name="hora-de-busqueda">
```

El campo `type="month"` permite al usuario introducir un mes y un año:

```html
<input type="month" name="mes-lanzamiento">
```

El campo `type="week"` permite al usuario introducir una semana y un año:

```html
<input type="week" name="elegir-semana">
```

Todos estos campos permiten limitar el rango y los incrementos entre valores. Recomiendo revisar la documentación de Mozilla Developer Network (MDN) para conocer los detalles de su funcionamiento.

El campo `type="datetime-local"` permite elegir una fecha y una hora.

```html
<input type="datetime-local" name="fecha-y-hora">
```

Aquí tiene una página en la que puede probarlos todos.

### Selección de color

Puede permitir que el usuario seleccione un color mediante el elemento `type="color"`:

```html
<input type="color" name="color-auto">
```

Puede establecer un valor por defecto usando el atributo `value`:

```html
<input type="color" name="color-auto" value="#000000">
```

El navegador se encargará de mostrar un selector de color.

### Rango

Este elemento muestra una barra deslizante que puede moverse desde un valor mínimo hasta un valor máximo:

```html
<input type="range" name="edad" min="0" max="100" value="30">
```

Opcionalmente, puede especificar el incremento entre valores mediante el atributo `step`:

```html
<input type="range" name="age" min="0" max="100" value="30" step="10">
```

### Teléfono

El campo `type="tel"` se usa para introducir un número de teléfono:

```html
<input type="tel" name="numero-telefono">
```

La ventaja de usar `tel` en lugar de `text` es que, en dispositivos móviles, normalmente se mostrará un teclado numérico.

Puede especificar un atributo `pattern` para realizar una validación adicional:

```html
<input type="tel" pattern="[0-9]{3}-[0-9]{8}" name="numero-telefono">
```

### Dirección

El campo `type="url"` se usa para introducir una dirección web.

```html
<input type="url" name="sitio-web">
```

Puede validarse usando el atributo `pattern`:

```html
<input type="url" name="website" pattern="https://.*">
```

## La etiqueta `textarea`

El elemento `textarea` permite a los usuarios introducir texto multilínea. A diferencia de `input`, requiere una etiqueta de clausura:

```html
<textarea></textarea>
```

Puede ajustar sus dimensiones mediante CSS, así como usando los atributos `rows` y `cols`:

```html
<textarea rows="20" cols="10"></textarea>
```

Como ocurre con otros controles de formulario, el atributo `name` determina el nombre del dato enviado al servidor:

```html
<textarea name="articulo"></textarea>
```

## La etiqueta `select`

Esta etiqueta se usa para crear un menú desplegable.

En él, el usuario puede elegir una de las opciones disponibles.

Cada opción se crea usando la etiqueta `option`. Se asigna un nombre al control y un valor a cada opción:

```html
<select name="color">
	<option value="rojo">Rojo</option>
	<option value="amarillo">Amarillo</option>
</select>
```

También puede deshabilitar alguna de las opciones:

```html
<select name="color">
	<option value="rojo" disabled>Rojo</option>
	<option value="amarillo">Amarillo</option>
</select>
```

También puede incluir una opción vacía:

```html
<select name="color">
	<option value="">None</option>
	<option value="rojo">Rojo</option>
	<option value="amarillo">Amarillo</option>
</select>
```

Las opciones pueden agruparse usando la etiqueta `optgroup`. Cada grupo tiene un atributo `label`:

```html
<select name="color">
	<optgroup label="Primarios">
		<option value="rojo">Rojo</option>
		<option value="amarillo">Amarillo</option>
		<option value="azul">Azul</option>
	</optgroup>
	<optgroup label="Otros">
		<option value="verde">Verde</option>
		<option value="rosa">Rosa</option>
	</optgroup>
</select>
```