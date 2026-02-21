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

## 1. Conceptos Base: Display y Modelo de Caja <a name="1-conceptos-base"></a>

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

---

## 3. Z-Index y Contexto de Apilamiento <a name="z-index"></a>

El `z-index` define qué elemento se muestra "encima" de otro en el eje Z (profundidad). 

> **Regla de oro:** Para que un `z-index` funcione, el elemento **debe** tener una propiedad `position` distinta a `static` (usualmente `relative` en el padre).


## 3. Z-Index y Contexto de Apilamiento <a name="z-index"></a>

El `z-index` define qué elemento se muestra "encima" de otro en el eje Z (profundidad). 

> **Regla de oro:** Para que un `z-index` funcione, el elemento **debe** tener una propiedad `position` distinta a `static` (usualmente `relative` en el padre).

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

**HTML:**
<div class="flex-container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>

**CSS:**
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


--- 

## 4. Flexbox: diseño unidimensional <a name="flexbox"></a>

Flexbox está diseñado para organizar elementos en un solo eje o dimensión (ya sea una fila o una columna).<br>
Se activa aplicando `display: flex;` al contenedor padre.



### 4.1 Propiedades del contenedor (padre)

* **`flex-direction`**: Define la dirección del flujo.
    * `row` (defecto): Horizontal de izquierda a derecha.
    * `column`: Vertical de arriba hacia abajo.
    * `row-reverse` / `column-reverse`: Invierte el orden de los elementos.
* **`flex-wrap`**: Controla qué sucede si los hijos no caben en una línea.
    * `nowrap` (defecto): Encoge los elementos para que entren forzosamente.
    * `wrap`: Los elementos saltan a la siguiente línea si no hay espacio.
* **`justify-content`**: Alineación en el **eje principal** (horizontal si es `row`).
    * `flex-start` | `center` | `flex-end` | `space-between` | `space-around` | `space-evenly`.
* **`align-items`**: Alineación en el **eje secundario** (vertical si es `row`).
    * `stretch` (defecto): Estira los hijos para llenar el contenedor.
    * `center` | `flex-start` | `flex-end`.
* **`gap`**: Define el espacio de separación entre los elementos hijos.


### 4.2 Propiedades de los hijos (items)

* **`flex-grow`**: Capacidad de un elemento para crecer y ocupar el espacio sobrante (ej. `flex-grow: 1;`).
* **`flex-shrink`**: Capacidad para encogerse si el contenedor es muy pequeño.
* **`flex-basis`**: El tamaño inicial de un elemento antes de que se distribuya el espacio libre.
* **`order`**: Permite cambiar el orden visual de un hijo (ej. `order: -1;` lo mueve al principio).

---

## 5. CSS Grid: Diseño Bidimensional <a name="grid"></a>

Mientras Flexbox piensa en una dirección, **Grid Layout** permite manejar filas y columnas simultáneamente. Es la herramienta definitiva para layouts de páginas completas.



### 5.1 Definición de la Cuadrícula
```css
.contenedor-grid {
  display: grid;
  /* Crea 3 columnas: una de 200px y dos que se reparten el resto (fr) */
  grid-template-columns: 200px 1fr 1fr;
  /* Crea filas automáticas según el contenido */
  grid-template-rows: auto;
  gap: 20px; /* Espacio entre filas y columnas */
}
```

### 5.2 Conceptos Avanzados de Grid <a name="grid-conceptos"></a>

Para dominar Grid, necesitas conocer estas herramientas que hacen que el diseño sea realmente "mágico" y adaptable:

* **Unidad `fr` (Fraction)**: Representa una fracción del espacio libre. Si tienes `1fr 2fr`, el segundo elemento ocupará el doble de espacio que el primero.
* **`repeat()`**: Evita escribir lo mismo varias veces. 
  * *Ejemplo:* `grid-template-columns: repeat(3, 1fr);` (Crea 3 columnas iguales).
* **`minmax()`**: Establece un tamaño mínimo y máximo para una celda.
  * *Ejemplo:* `grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));` (Crea columnas que nunca miden menos de 200px y se ajustan solas).
* **`grid-template-areas`**: Es la forma más visual de maquetar. Le das nombre a tus elementos y "dibujas" la estructura.



```css
.layout {
  display: grid;
  grid-template-areas: 
    "header header"
    "nav main"
    "footer footer";
}

.header { grid-area: header; }
.sidebar { grid-area: nav; }
.contenido { grid-area: main; }
.footer { grid-area: footer; }
```


### 5.2 Conceptos Avanzados de Grid <a name="grid-conceptos"></a>

Para dominar Grid, necesitas conocer estas herramientas que hacen que el diseño sea realmente "mágico" y adaptable:

* **Unidad `fr` (Fraction)**: Representa una fracción del espacio libre. Si tienes `1fr 2fr`, el segundo elemento ocupará el doble de espacio que el primero.
* **`repeat()`**: Evita escribir lo mismo varias veces. 
  * *Ejemplo:* `grid-template-columns: repeat(3, 1fr);` (Crea 3 columnas iguales).
* **`minmax()`**: Establece un tamaño mínimo y máximo para una celda.
  * *Ejemplo:* `grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));` (Crea columnas que nunca miden menos de 200px y se ajustan solas).
* **`grid-template-areas`**: Es la forma más visual de maquetar. Le das nombre a tus elementos y "dibujas" la estructura.



```css
.layout {
  display: grid;
  grid-template-areas: 
    "header header"
    "nav main"
    "footer footer";
}

.header { grid-area: header; }
.sidebar { grid-area: nav; }
.contenido { grid-area: main; }
.footer { grid-area: footer; }
```



## 🛠️ Resumen Comparativo: ¿Qué herramienta usar?

Maquetar no se trata de elegir una sola herramienta, sino de combinarlas según el problema. Aquí tienes una regla rápida para decidir:

| Situación | Herramienta Ideal | Por qué |
| :--- | :--- | :--- |
| **Superponer** elementos (un badge sobre una foto). | `position: absolute` | Saca al elemento del flujo normal del documento. |
| **Menú** de navegación o alinear iconos/botones. | **Flexbox** | Control total sobre la alineación y el espacio en un solo eje. |
| **Layout principal** (Header, Sidebar, Main, Footer). | **CSS Grid** | Control bidimensional perfecto (filas y columnas a la vez). |
| **Barra superior** que te sigue al hacer scroll. | `position: sticky` | Mantiene el elemento visible dentro de su contenedor padre. |



---

## 🚀 Conclusión y Siguientes Pasos

Dominar la maquetación moderna es la base de cualquier frontend. No intentes memorizar cada propiedad; lo más importante es entender **la jerarquía entre contenedores (padres) e hijos**.



> **💡 Consejo de un par:** Cuando algo no se alinee como esperas, abre las herramientas de desarrollador (`F12` o `Click derecho > Inspeccionar`) y busca las etiquetas **flex** o **grid** junto a los elementos. El navegador te mostrará las líneas guía y el espacio de los "gaps", lo cual es clave para debugear visualmente.

---

### 🎨 ¿Qué te gustaría practicar ahora?
¿Quieres que te pase el **código HTML/CSS** de un ejemplo real que combine las tres técnicas (por ejemplo, una "Card de Producto" con precio flotante), o prefieres que veamos cómo hacer este diseño **Responsive** para móviles?







"Pásame la tabla X en un bloque de código (o chunk) de texto plano."