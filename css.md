## Archivo CSS
### Ejemplos de estilos en un archivo .css

```css
/*Esto es un comentario en .css*/

/*Los estilos van entre '{}' y se separan con ';' */
body {
    margin: 0;
    color: black;
}
```

## Referencias al HTML:
### Para añadir estilos a `<tags>` usamos código CSS

```css
/*Esto añade estilos a cualquier tag `<div>`*/
div {
```

```css
/*Esto añade estilos al **id**: `<div id="unico">`*/
#unico {
```

```css
/*Estilos en: `<div class="generica">`*/
.generica {
```

```css
/*Cualquier <td> en: `<table id="tabla"><tr><td>..`*/
#tabla td {
```

```css
/*Cualquier <td> hijo directo de <tr>: `<tr><td>..`*/
tr > td {
```

```css
/*Puedes referenciar múltiples elementos con comas*/
button, .label > a, #formulario input {
```

```css
/*Se activa cuando pones el mouse encima*/
button:hover {
```

```css
/*Se activa cuando precionas con el mouse*/
button:focus {
```

```css
/*Elemento antes `::before` o después `::after`
  Debe contener al menos el atributo: `content:`*/
button::before { | button::after {
  content: " ";
```

## Valores CSS genéricos

```css
: initial;          /*deja la propiedad por defecto*/
: inherit;         /*hereda la propiedad del parent*/
```

## Colores e Imágenes

Existen varias maneras de definir un mismo <span style="color:red">color</span> en css:

| nombre | RGB          | RGB+A (alpha)   | HEX     |
|--------|--------------|-----------------|---------|
| red    | rgb(255,0,0) | rgba(255,0,0,1) | #ff0000 |

```css
color: red;                           /*color texto*/
```

```css
background-color: red;                /*color fondo*/
background:
  linear-gradient(red,yellow);   /*gradiente lineal*/
  radial-gradient(red,yellow);   /*gradiente radial*/
background-size: cover;             /*tamaño imagen*/
```

```css
background-image: url(ruta.jpg);     /*imagen fondo*/
background-poistion: 50%;         /*posicion imagen*/
background-repeat: no-repeat;   /*repetición imagen*/
background-size: cover;             /*tamaño imagen*/
```

## Textos y Fuentes
```css
font-family: sans-serif;                   /*fuente*/
font-size: 16px;                           /*tamaño*/
font-style: italic;                        /*estilo*/
font-weight: bold;                         /*grueso*/
```

```css
text-align: center;      /*alinea horizontal (todo)*/
text-decoration: underline;            /*decoración*/
text-overflow: ellipsis;             /*al desbordar*/
text-transform: uppercase;   /*en mayusc. o minusc.*/
text-shadow: 1px 1px black;                /*sombra*/
```

```css
white-space: nowrap;          /*sin saltos de linea*/
word-break: break-all;/*parte palabras entre líneas*/
word-spacing: 1px;         /*espacio entre palabras*/
```

```css
vertical-align: middle; /*alinea elementos vertical*/
```

---

## Border, Padding y Margin 
### top, bottom, left, right

```css
border: 1px solid black;         /*todos los bordes*/
border-top: 1px solid black;  /*solo el borde 'top'*/
border-radius: 5px;       /*redondear contenido 5px*/
```

```css
padding: 5px;       /*margen interior del contenido*/
padding-right: 5px;            /*5px (lado derecho)*/
```

```css
margin: 5px;         /*margen exterior al contenido*/
margin-left: 5px;            /*5px (lado izquierdo)*/
```

```css
border-width: | padding: | margin:    /*Dimensiones*/
  5px;                        /*tamaño de 5 píxeles*/
  0 5px;          /*tamaños top/bottom y left/right*/
  5px 0 5px 0;       /*orden: top right bottom left*/
```

![paddings y margins](https://www.beginnersguidetohtml.com/images/boxmodel.gif)

```css
box-shadow:                   /*sombra del elemento*/
  1px 1px 5px black; /*1px top-left, 5px difuminado*/
inset 1px 1px 5px black;      /*mismo pero interior*/
```

## Usuario

```css
cursor: pointer;       /*cambia el icono del cursor*/
user-select: none; /*deshabilita seleccion de texto*/
```

## Transformaciones

```css
width: 100%;                                /*ancho*/
height: 100px; /*% solo si parent tiene altura fija*/
```

```css
position:
  fixed;             /*posicion fija de la pantalla*/
  absolute;            /*posicion fija de la pagina*/
  relative:  /*tags 'absolute' son relativos a este*/
```

```css
/* solo para elementos con atributo 'position': */
top: 0;                  /*margen absoluto superior*/
bottom: 0;               /*margen absoluto inferior*/
left: 0;                /*margen absoluto izquierdo*/
right: 0;                 /*margen absoluto derecho*/
```

```css
display:
  block;       /*el elemento se comporta como <div>*/
  inline-block; /*como <div> pero de ancho variable*/
  none;          /*oculta el elemento y sus efectos*/
```

```css
float:
  left;    /*lo lleva a la izquierda del contenedor*/
  right;     /*lo lleva a la derecha del contenedor*/
```

```css
transform:
  translate(-50%, -50%);    /*% de su propio tamaño*/
  translateX(-100%);   /*mueve el elemento en eje X*/
  translateY(-100%);   /*mueve el elemento en eje Y*/
  rotate(90deg);    /*rota el elemento (deg=grados)*/
```

```css
box-sizing: border-box;  /*que tamaño incluya borde*/
table-layout: fixed;     /*se fijan anchos de tabla*/
border-collapse: collapse; /*quita espaciados tabla*/
```

```css
overflow-x: | overflow-y: /*contenido que sobresale*/
  auto;             /*muestra scroll si lo necesita*/
  visible;           /*se muestra aunque sobresalga*/
  hidden;                /*oculta lo que sobresalga*/
  scroll;               /*siempre muestra el scroll*/
```

```css
z-index: 99;  /*antepone los elementos unos a otros*/
```

```css
transition: all 300ms;  /*tiempo transición cambios*/
```
