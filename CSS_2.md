# 🌐 Guía de Referencia Rápida: CSS Maquetación Moderna

Esta guía resume los fundamentos de maquetación con CSS. <br>
Para una consulta técnica profunda, siempre es recomendable visitar la documentación oficial.

> 📚 **Documentación recomendada:**
> * **[MDN Web Docs - CSS](https://developer.mozilla.org/es/docs/Web/CSS)**
> * **[W3Schools - Tutorial CSS](https://www.w3schools.com/css/)**

---

## 🔍 Índice de Contenidos
1. [Conceptos Base: Display y Modelo de Caja](#1-conceptos-base)
2. [Posicionamiento (`position`)](#2-posicionamiento)
3. [Z-Index y Apilamiento](#3-z-index)
4. [Flexbox: Diseño Unidimensional](#4-flexbox)
5. [CSS Grid: Diseño Bidimensional](#5-css-grid)

---

## 1. Conceptos Base: display y Modelo de Caja <a name="1-conceptos-base"></a>

Lo que se desarrollará requiere conocimiento previo del modelo de la caja.<br>
Recordemos que tenemos dos tipos de elementos:
* `div` elementos en bloque
* `span` elementos en línea
Si cambiamos las propiedades background (color), width y height de un `span` no notaremos cambio en su tamaño por ser un bloque inline.<br>
Para cambiar un elemento en línea a en bloque existe la propiedad: `display`: inline/block; 
<br>
En la guía vamos a ver cómo trabajar con la propiedad `display` para ordenar el contenido a nuestro gusto: inline, block, **flex** y **grid**.



### Propiedad display (comportamiento de la caja)
Antes de ordenar cajas, debemos entender cómo se comportan.<br>
Los valores que puede tener la propiedad `display` (colocada en el elemento contenedor) son:

| Valor | Descripción | Comportamiento | Ejemplos Comunes |
| :--- | :--- | :--- | :--- |
| **`block`** | Ocupa todo el ancho disponible. | Salto de línea automático. Acepta `width` y `height`. | `div`, `h1`, `p`, `section` |
| **`inline`** | Ocupa solo el ancho de su contenido. | Se mantiene en la misma línea. **Ignora** `width` y `height`. | `span`, `a`, `strong` |
| **`inline-block`** | Híbrido entre block e inline. | Se mantiene en línea pero **permite** definir tamaños y márgenes. | `button`, `input` |
| **`none`** | Elimina el elemento del DOM. | El elemento desaparece y **no ocupa espacio** en el layout. | Menús desplegables (ocultos) |
| **`flex` / `grid`** | Activa contextos de layout. | Convierte al elemento en contenedor para alinear a sus hijos. | Navbar, Galerías, Layouts |


### Repaso del Modelo de Caja

| Capa | Descripción | Función Clave |
| :--- | :--- | :--- |
| **`Content`** | El área central de la caja. | Contiene el texto, imágenes o hijos. |
| **`Padding`** | Espacio **interno**. | Separa el contenido del borde (da "aire"). |
| **`Border`** | Límite físico de la caja. | Envuelve el padding y el contenido. |
| **`Margin`** | Espacio **externo**. | Separa el elemento de sus cajas vecinas. |


Para evitar que el `padding` y el `border` expandan el tamaño real de tus cajas, usa siempre:

| Propiedad | Valor | Efecto |
| :--- | :--- | :--- |
| **`box-sizing`** | `border-box` | El `width` total ya incluye el padding y el border. |
| **`box-sizing`** | `content-box` | (Default) El padding y el border se **suman** al `width` definido. |


```css
* {
  box-sizing: border-box; /* El tamaño declarado es el tamaño final real */
}
```



---

## 2. Posicionamiento: Atributo `position` <a name="posicionamiento"></a>

La propiedad `position` determina cómo se ubica un elemento en el documento. Por defecto, las cajas se ubican de arriba a abajo y de izquierda a derecha (`static`).

| Valor | Descripción |
| :--- | :--- |
| **`static`** | El valor por defecto. Sigue el flujo normal del HTML. |
| **`relative`** | Se mueve respecto a su posición original. Se usa como **punto de referencia** (ancla) para hijos con posición absoluta. |
| **`absolute`** | Se posiciona respecto al pariente más cercano con `position: relative`. Sale del flujo normal y no ocupa espacio. |
| **`fixed`** | Queda anclado a la pantalla (viewport). No se mueve aunque hagas scroll (ej. botones de chat). |
| **`sticky`** | Se queda "pegado" en una posición relativa mientras su contenedor sea visible en pantalla. |


### Ejemplo práctico: Comportamiento de Cajas con `position`


```html
<div class="container">
  <div class="box">Caja 1 (Relative)</div>
  <div class="box">Caja 2 (Relative)</div>
  <div class="box">Caja 3 (Relative)</div>
</div>
```

```css
/* Contenedor para dar contexto al posicionamiento */
.container {
  position: relative;
  width: 100%;
  height: 400px;
  background-color: #f4f4f4;
  border: 2px solid #333;
  padding: 10px;
}

/* Estilo base para todas las cajas */
.box {
  width: 100px;
  height: 100px;
  color: white;
  display: flex;
  margin-bottom: 10px;
}

/* Selección por n-child para modificar cada una */
.box:nth-child(1) {
  background-color: red; 
  position: relative;
}

.box:nth-child(2) {
  background-color: blue; 
  position: relative;
}

.box:nth-child(3) {
  background-color: green; 
  position: relative;
}
```


---

## 3. Z-Index y Contexto de Apilamiento <a name="z-index"></a>

El `z-index` define qué elemento se muestra "encima" de otro en el eje Z (profundidad). 

> **Recordatorio:** Para que un `z-index` funcione, el elemento **debe** tener una propiedad `position` distinta a `static` (usualmente `relative` en el padre).

```html
<div class="escenario">
  <div class="capa capa-1">Z-Index: 1</div>
  <div class="capa capa-2">Z-Index: 10</div>
  <div class="capa capa-3">Z-Index: 5</div>
</div>
```


```css
.contenedor-padre {
  position: relative; /* Contexto de apilamiento */
}

.caja-delantera {
  position: absolute;
  z-index: 10; /* Valor más alto, se ve primero */
}

.caja-fondo {
  position: absolute;
  z-index: 1; /* Valor bajo, queda detrás */
}
```


---

## 4. Flexbox: diseño unidimensional <a name="flexbox"></a>

Flexbox organiza elementos en un solo eje (fila o columna). Se activa con `display: flex;` en el contenedor padre.

### 4.1 Propiedades del Contenedor (padre)

| Propiedad | Valores comunes | Efecto |
| :--- | :--- | :--- |
| **`flex-direction`** | `row`, `column`, `row-reverse` | Define la dirección del eje principal. |
| **`flex-wrap`** | `nowrap`, `wrap` | Define si los hijos saltan a una nueva línea. |
| **`justify-content`** | `center`, `space-between`, `gap` | Alinea los hijos en el **eje principal**. |
| **`align-items`** | `center`, `stretch`, `flex-end` | Alinea los hijos en el **eje secundario**. |
| **`gap`** | `10px`, `1rem` | Define el espacio exacto entre los hijos. |



### 4.2 Propiedades de los hijos (items)

| Propiedad | Función | Uso típico |
| :--- | :--- | :--- |
| **`flex-grow`** | Capacidad de crecer. | `flex-grow: 1` para ocupar espacio sobrante. |
| **`flex-shrink`** | Capacidad de encogerse. | `0` para evitar que el elemento se deforme. |
| **`flex-basis`** | Tamaño inicial. | Define el ancho/alto base antes del stretch. |
| **`order`** | Orden visual. | Cambia la posición sin tocar el HTML. |

### Ejemplo: Estructura de tarjetas con flexbox

ejemplo flexbox HTML
```html
<div class="flex-container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>
```

ejemplo flexbox CSS
```css
.flex-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 15px;
  background: #2c3e50;
  padding: 20px;
}

.item {
  flex: 1; /* Atajo para grow, shrink y basis */
  height: 100px;
  background: #ecf0f1;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

---

---

## 5. CSS Grid: Diseño Bidimensional <a name="5-css-grid"></a>

CSS Grid es el sistema de maquetación más potente de CSS. A diferencia de Flexbox (unidimensional), Grid es **bidimensional**, permitiendo controlar filas y columnas al mismo tiempo. Se usa principalmente para estructuras complejas de layouts y galerías de eventos.



### 5.1 Propiedades del Contenedor (Padre)

| Propiedad | Descripción | Valores comunes / Ejemplos |
| :--- | :--- | :--- |
| **`display: grid`** | Activa el contexto de rejilla. | Se observa la cuadrícula en el inspector web. |
| **`grid-template-columns`** | Define el ancho de las columnas. | `200px 1fr 1fr`, `repeat(3, 1fr)` |
| **`grid-template-rows`** | Define el alto de las filas. | `100px auto 200px` |
| **`grid-auto-rows`** | Alto para filas creadas automáticamente. | `minmax(100px, auto)` |
| **`justify-items`** | Alinea contenido dentro de la celda (H). | `start`, `center`, `end`, `stretch` |
| **`align-items`** | Alinea contenido dentro de la celda (V). | `start`, `center`, `end`, `stretch` |
| **`gap`** | Espacio entre celdas. | `10px`, `1rem 2rem` (fila columna) |

### 💡 Herramientas Clave: fr, repeat y minmax

* **Unidad `fr`**: Fracción del espacio libre. Si tienes `1fr 2fr`, la segunda columna será el doble de ancha.
* **`repeat(n, valor)`**: Repite un patrón. `repeat(12, 1fr)` crea 12 columnas iguales.
* **`minmax(min, max)`**: Garantiza que una celda no colapse. `minmax(200px, 1fr)` nunca medirá menos de 200px.
* **`auto-fill` / `auto-fit`**: Permite que el navegador decida cuántas columnas caben según el tamaño de pantalla.

### 5.2 Propiedades de los Hijos (Items)

Grid permite posicionar elementos en cualquier sitio, ¡incluso encimarlos sin usar `position` absoluto!

| Propiedad | Descripción | Uso con `span` |
| :--- | :--- | :--- |
| **`grid-column-start`** | Línea donde inicia la columna. | `1` |
| **`grid-column-end`** | Línea donde termina la columna. | `3` (termina en la línea 3) |
| **`grid-column`** | Atajo (start / end). | `1 / 4` o `1 / span 3` (ocupa 3 celdas) |
| **`grid-row`** | Atajo para filas. | `2 / span 2` (ocupa 2 filas) |

### 🕹️ Ejemplo: Layout de 11 bloques

**HTML:**
<div class="grid-layout">
  <div class="item">1</div>
  <div class="item main">2 (Principal)</div>
  <div class="item">3</div>
  <div class="item">4</div>
  <div class="item">5</div>
  <div class="item">6</div>
  <div class="item">7</div>
  <div class="item">8</div>
  <div class="item">9</div>
  <div class="item">10</div>
  <div class="item">11</div>
</div>

**CSS:**
.grid-layout {
  display: grid;
  grid-template-columns: repeat(4, 1fr); /* 4 columnas iguales */
  grid-auto-rows: minmax(100px, auto);
  gap: 10px;
}

.main {
  grid-column: span 2; /* Ocupa 2 columnas */
  grid-row: span 2;    /* Ocupa 2 filas */
  background-color: #f39c12 !important;
}

.item {
  background-color: #3498db;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid #2980b9;
}

---

## 6. Media Queries: Diseño Responsivo <a name="media-queries"></a>

Las Media Queries permiten aplicar estilos diferentes según las características del dispositivo (principalmente el ancho de pantalla). Es lo que hace que un sitio sea **Mobile First**.



### Sintaxis Básica

```css
/* Estilos generales (Mobile por defecto) */
.layout {
  display: flex;
  flex-direction: column;
}

/* Tablet y Desktop (Pantallas mayores a 768px) */
@media (min-width: 768px) {
  .layout {
    flex-direction: row;
    background-color: lightblue;
  }
}

"Pásame la tabla X en un bloque de código (o chunk) de texto plano."