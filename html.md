## HTML
### Plantilla de ejemplo de una página .html tipo

```html
<!doctype html>
<html>
  <!--Esto es un comentario en HTML-->
  <!--Un comentario no afecta al código-->

  <!--en <head> cargamos código externo-->
  <head>
    <!--los <meta> son datos del doc. HTML-->

    <!--ej: charset="utf-8" dice al navegador 
    como mostrar correctamente los acentos-->
    <meta charset="utf-8">

    <title>Título de la pag. web</title>

    <!--cargamos estilos .css con <link>-->
    <link rel="stylesheet" href="ruta.css">

    <!--cargamos código .js con <script>-->
    <script src="asíncrono.js"></script>

    <!--añadimos estilos .css con <style>-->
    <style>
      .nombre_de_clase {
        color: red;
        margin: 10px;
      }
    </style>

    <!--añadimos código .js con <script>-->
    <script>
      var una_variable = "un_texto";
      //esto es un comentario javascript
    </script>
  </head>

  <!--el <body> es la parte que se muestra-->
  <body>
    <!--el resto de código HTML viene aquí-->

    <!--para cargar js al final-->
    <script src="sincrónico.js"></script>
  </body>

</html>
```

## Tags comunes
### Para construir páginas web en <b>.html</b> usamos tags < >

| `<div>contenido</div>`
| :--
| Agrupar el HTML en elementos separados (**div**isiones)

| `<p>texto</p>`
| :--
| Elementos de texto que añaden márgenes (**p**árrafos)

| `<span>palabras</span>`
| :--
| Agrupaciones de texto para añadir <span style="color: darkgrey; font-weight: bold; text-shadow: 1px 1px black; font-style: italic; font-family: sans-serif;">atributos</span> en texto

| `<a href="ruta.html">un link</a>`
| :--
| Para hacer <a style="color:blue;text-decoration:underline">un link</a> (**a**nchor)

| `<button>haz clik en el botón</button>`
| :--
| <button>haz clik en el botón</button>

| `<img src="ruta.jpg">`
| :--
| Muestra la imagen de la ruta: &nbsp; <img src="ruta.jpg" style="position: absolute; margin-top: -7px; width: 20px; height: 20px;">

| `<br>`
| :--
| Elemento para continuar en la siguiente línea como un 'enter' (Introducir lineas solo con 'enter' en html no tiene efecto)

| `<b></b>`    | `<i></i>`     | `<u></u>`        | `<s></s>`     |
| ------------ | ------------- | ---------------- | ------------- |
| <b>bold</b>  | <i>italic</i> | <u>underline</u> | <s>strike</s> |

---

## Tags inputs
### los inputs sirven para que el usuario pueda introducir y datos

```html
<input type="[...]" placeholder="escribe aquí">
```

| `type="text"` | `type="checkbox"` | `type="radio"` |
| --------- | --------- | ------------- |
| <input type="text" placeholder="escribe aquí" style='width: 100%;'> | <input type="checkbox" style="vertical-align: middle"> | <input type="radio" style="vertical-align: middle"> |

| `<textarea>Texto multi-linea</textarea>`
| :--
| <textarea rows="1" style="width: 100%; resize: vertical; background-color: rgba(255,255,255,0.5)">Texto multi-linea</textarea>

```html
<option value="1">
    opción 1
</option>
<option value="2">
    opción 2
</option>
```
Desplegable multi-opción:
<select>
    <option value='1'>opción 1</option>
    <option value='2'>opción 2</option>
</select>

## Tag tabla
###  nota: las tablas NUNCA se usan para organizar la pag. web

```html
<table>
  <!--cabecera: (opcional agregar <thead>)-->
  <thead>
    <!-- columna: -->
    <tr>
      <!-- celdas: -->
      <th>contenido cabecera 1</th>
      <th>contenido cabecera 2</th>
    </tr>
  </thead>
  <!--cuerpo: (opcional definir <tbody>)-->
  <tbody>
    <tr>
      <td>contenido celda 3</td>
      <td>contenido celda 4</td>
    </tr>
    <tr>
      <td>contenido celda 5</td>
      <td>contenido celda 6</td>
    </tr>
  </tbody>
</table>
```

<table class="table_example">
    <thead style="font-weight: bold">
        <tr>
            <th>contenido cabecera 1</th>
            <th>contenido cabecera 2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>contenido celda 3</td>
            <td>contenido celda 4</td>
        </tr>
        <tr>
            <td>contenido celda 5</td>
            <td>contenido celda 6</td>
        </tr>
    </tbody>
</table>

## Atributos
### Los atributos html son propiedades que se añaden en tags

| `<div id="único" class='genérico'>`
| :--
| **'id'** y **'class'** permiten encontrar dichos &lt;tag&gt; desde el código

| `<span style="color:green; font-weight:bold">`
| :--
| **'style'** añade <span style="color:green; font-weight:bold">estilos</span> en el contenido del &lt;tag&gt;

| `<button title="This is a tooltip">OK</button>`
| :--
| <button title="This is a tooltip">OK</button> **'title'** muestra un pop-up con la información. Puede usarse sobre cualquier tipo de `<tag>`
