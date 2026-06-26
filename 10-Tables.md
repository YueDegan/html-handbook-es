# Tablas

En los primeros días de la web, las tablas eran una parte importante en la construcción de interfaces.

Posteriormente fueron reemplazadas por CSS y sus capacidades para crear interfaces. Hoy contamos con herramientas muy potentes, como CSS Grid y Flexbox, para construir interfaces. En la actualidad, las tablas se usan para lo que fueron diseñadas: ¡crear tablas!

## La etiqueta `table`

Puede definir una tabla usando la etiqueta `table`:

```html
<table>

</table>
```

Dentro de la tabla definiremos los datos. Debemos pensar en términos de filas, lo que significa que lo que se agrega a una tabla son filas, no columnas. Las columnas se definen dentro de cada fila.

## Filas

Una fila se agrega usando la etiqueta `tr`:

```html
<table>
  <tr></tr>
  <tr></tr>
  <tr></tr>
</table>
```

Esta es una tabla con tres filas.

La primera fila *puede* desempeñar el papel de encabezado.

## Encabezados de columna

El encabezado de una tabla contiene el nombre de una columna, normalmente mostrado en negrita.

Piense en una hoja de cálculo de Excel o Google Sheets. Es similar a los encabezados `A-B-C-D...` de la parte superior.

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.18.17.png)

El encabezado se define usando la etiqueta `th`:

```html
<table>
  <tr>
    <th>Columna 1</th>
    <th>Columna 2</th>
    <th>Columna 3</th>
  </tr>
  <tr></tr>
  <tr></tr>
</table>
```

## Contenido de una tabla

El contenido de una tabla se define usando etiquetas `td` dentro de los elementos `tr`:

```html
<table>
  <tr>
    <th>Columna 1</th>
    <th>Columna 2</th>
    <th>Columna 3</th>
  </tr>
  <tr>
    <td>Fila 1 Columna 1</td>
    <td>Fila 1 Columna 2</td>
    <td>Fila 1 Columna 3</td>
  </tr>
  <tr>
    <td>Fila 2 Columna 1</td>
    <td>Fila 2 Columna 2</td>
    <td>Fila 2 Columna 3</td>
  </tr>
</table>
```

Los navegadores la renderizan de la siguiente manera si no se le aplican estilos con CSS:

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.24.08.png)

Agregar el siguiente CSS:

```css
th, td {
  padding: 10px;
  border: 1px solid #333;
}
```

hace que la tabla tenga un aspecto más tradicional:

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.26.15.png)

## Tamaño de filas y columnas

Una celda puede expandirse a dos o más columnas usando el atributo `colspan`:

```html
<table>
  <tr>
    <th>Columna 1</th>
    <th>Columna 2</th>
    <th>Columna 3</th>
  </tr>
  <tr>
    <td colspan="2">Fila 1 Columnas 1-2</td>
    <td>Fila 1 Columna 3</td>
  </tr>
  <tr>
    <td colspan="3">Fila 2 Columnas 1-3</td>
  </tr>
</table>
```

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.27.59.png)

También puede expandirse a dos o más filas usando el atributo `rowspan`:

```html
<table>
  <tr>
    <th>Columna 1</th>
    <th>Columna 2</th>
    <th>Columna 3</th>
  </tr>
  <tr>
    <td colspan="2" rowspan="2">Filas 1-2 Columnas 1-2</td>
    <td>Fila 1 Columna 3</td>
  </tr>
  <tr>
    <td>Fila 2 Columna 3</td>
  </tr>
</table>
```

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.29.37.png)

## Encabezados de fila

Anteriormente expliqué cómo crear encabezados de columna usando la etiqueta `th` dentro de la primera fila (`tr`) de la tabla.

También puede agregar una etiqueta `th` como el primer elemento de cualquier otra fila para crear encabezados de fila:

```html
<table>
  <tr>
    <th></th>
    <th>Columna 2</th>
    <th>Columna 3</th>
  </tr>
  <tr>
    <th>Fila 1</th>
    <td>Col 2</td>
    <td>Col 3</td>
  </tr>
  <tr>
    <th>Fila 2</th>
    <td>Col 2</td>
    <td>Col 3</td>
  </tr>
</table>
```

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.49.16.png)

## Más etiquetas para organizar las tablas

Existen tres etiquetas adicionales que pueden agregarse a una tabla para organizar mejor su estructura.

Son especialmente útiles en tablas grandes, ya que permiten definir claramente el encabezado, el cuerpo y el pie de la tabla.

Estas etiquetas son:

- `thead`
- `tbody`
- `tfoot`

Agrupan las etiquetas `tr` para definir claramente las distintas secciones de la tabla. Por ejemplo:

```html
<table>
  <thead>
    <tr>
      <th></th>
      <th>Columna 2</th>
      <th>Columna 3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Fila 1</th>
      <td>Col 2</td>
      <td>Col 3</td>
    </tr>
    <tr>
      <th>Fila 2</th>
      <td>Col 2</td>
      <td>Col 3</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td></td>
      <td>Pie de Columna 2</td>
      <td>Pie de Columna 3</td>
    </tr>
  </tfoot>
</table>
```

![](9-Tables/Screen%20Shot%202019-06-20%20at%2010.52.41.png)

## Descripción de una tabla

Una tabla debería tener una etiqueta `caption` que describa su contenido. Esta etiqueta debe agregarse inmediatamente después de la etiqueta `table`:

```html
<table>
  <caption>Edades de los perritos</caption>
  <tr>
    <th>Perrito</th>
    <th>Edad</th>
  </tr>
  <tr>
    <td>Solovino</td>
    <td>7</td>
  </tr>
</table>
```