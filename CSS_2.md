# 🌐 Guía de Referencia Rápida: CSS Maquetación Moderna con Position, Flexbox y Grid

Esta guía está diseñada para proporcionar los fundamentos de la maquetación con CSS. <br>
Para una consulta profunda y técnica, siempre es recomendable visitar la documentación oficial.

> 📚 **Documentación recomendada:** Para profundizar en cada propiedad y ver ejemplos interactivos, te recomendamos visitar:
>* **[MDN Web Docs - CSS](https://developer.mozilla.org/es/docs/Web/CSS)**: La referencia técnica más completa y actualizada mantenida por la comunidad de Mozilla.
>* **[W3Schools - Tutorial CSS](https://www.w3schools.com/css/)**: Ideal para aprendizaje rápido con ejemplos interactivos y editores en vivo.

---

## 🔍 Índice de Contenidos


---

Lo que se desarrollará requiere conocimiento previo del modelo de la caja.<br>
Recordemos que tenemos dos tipos de elementos:
* `div` elementos en bloque
* `span` elementos en línea
Si cambiamos las propiedades background (color), width y height de un `span` no notaremos cambio en su tamaño por ser un bloque inline.<br>
Para cambiar un elemento en línea a en bloque existe la propiedad: `display`: inline/block; 
<br>
En la guía vamos a ver cómo trabajar con la propiedad `display` para ordenar el contenido a nuestro gusto: inline, block, **flex** y **grid**.

---

Repaso modelo de la caja:<br>
Sumar tamaños de contenido (width y height), border*2 y padding*2 (alteran el tamaño de la caja).<br>
No sumar margin (no modifica el tamaño de la caja pero sí su ubicación).<br>
<br>
Revisar en guía anterior sección con ejemplo: ¿Por qué usar `border-box`? <br>
box-sizing: border-box
<br>
Revisar documentación de overflow para el caso de desbordamiento de contenido (text-overflow: ellipsis;).

---




## Posiciones de cajas dentro de CSS

Por defecto, las cajas se ubican de arria a abajo y de derecha a izquierda.<br>
position: static; (valor por defecto)

Valores posibles para position:<br>
* {position:static;} (por defecto)<br>
* {position:absolute;} (top, right, left, bottom): Posiciona respecto del documento y no el elemento que lo contiene.<br>
* {position:relative;} Se debe colocar en el elemento que contiene a los restantes. Hace que los posicionamientos de los restantes elementos sean relativos. Punto relativo para que todos los hijos lo tengan de referencia.<br>
* {position:fixed;} Convierte a cada elemento hijo relativo a la pantalla/viewport (ejemplo para llamadas de whatsapp o chats).<br>
* {position:sticky;} Queda pegado en la posición relativa del elemento padre mientras se encuentre visible.




---

## Z-Index
Comentar contexto de aplilamiento y un ejemplo en el que pongamos un segundo elemento por debajo del que figura antes.<br>
Para usar la propiedad z-index debemos tener {position:relative;} en el padre

```zindex
generar ejemplo con HTML y CSS en el que se pueda modificar el z-index con 3 elementos para que quede uno delante del otro y se pueda modificar
```


---

## Flex
Si bien lo que más se suele utilizar es Grid veremos Flex que es aplicable a muchas situaciones.<br>
{display:flex;} se debe colocar en el contenedor (no en los hijos). A partir de ahí tendremos un contenedor flexible en el que podemos ordenar los contenedores hijo.<br>
<br>

### flex-direction
La dirección en la que se puede apilar el contenido es unidireccional: en fila/horizontal (valor por defecto) o en columnas/vertical.
* {flex-direction:row;} Valor por defecto para filas.
* {flex-direction:column;} Valor por defecto para columnas.
* {flex-direction:row-reverse;} Ordenar desde el último hacia el primero por fila.
* {flex-direction:column-reverse;} Ordenar desde el último hacia el primero por columna.

### flex-wrap
Al igual que la propiedad flex-direction se debe colocar en el elemendo contenedor.<br>
Su función es hacer que los elementos hijo entren en el contenedor padre.

* {flex-wrap:nowrap;} Valor por defecto para que el contenido no desborde al contenedor y tampoco genera nuevas filas.
* {flex-wrap:wrap;} Si el contenido no entra en el contenedor se genera una nueva fila.

```wrap
hacer un ejemplo con 3 a 9 child para que se pueda ir tocando la propiedad flex-wrap e ir tocando y viendo los cambios
```


### flex-grow, flex-shrink, flex-basis
Por defecto los elementos no crecen, pero en ocaciones necesitamos que se expandan a todo el espacio disponible del contenedor.<br>
REALIZAR UNA EXPLICACIÓN SIMPLE.<br>
EN CASO DE QUE SEA DE UTILIDAD O APORTAR VALOR EXPLICAR flex y order.<br>
<br>


### justify-content y aling-content

Forma de posicionar y alinear los elementos con flexbox.<br>
center(valor por defecto), space-arround(ocupa todo el eje row o column equiespaciado), flex-start, flex-end,flex-center<br>
Otra forma de generar espaciado es con la propiedad gap.<br>



```justify-content
hacer un ejemplo con 3 a 9 child para que se pueda ir tocando la propiedad justify-content, flex-direction y aling-content para ir tocando y viendo los cambios
```


---




---

## Grid


---




---




---




# 🌐 Guía de Referencia Rápida: CSS Maquetación Moderna

Esta guía resume los fundamentos de maquetación con CSS. Para una consulta técnica profunda, siempre es recomendable visitar la documentación oficial.

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

Antes de ordenar cajas, debemos entender cómo se comportan:

* **`display: block`**: Ocupan todo el ancho y saltan de línea (ej. `div`, `h1`, `p`).
* **`display: inline`**: Solo ocupan el ancho de su contenido y no aceptan `width` o `height` (ej. `span`, `a`).
* **`display: inline-block`**: Se alinean en línea pero permiten definir tamaños.

### 📦 Repaso del Modelo de Caja
Para que el `padding` y el `border` no aumenten el tamaño total de tus elementos, usa siempre:

```css
* {
  box-sizing: border-box; /* El tamaño declarado es el tamaño final real */
}
```


---

## 2. Posicionamiento (`position`) <a name="posicionamiento"></a>

La propiedad `position` determina cómo se ubica un elemento en el documento. Por defecto, las cajas se ubican de arriba a abajo y de izquierda a derecha (`static`).

| Valor | Descripción |
| :--- | :--- |
| **`static`** | El valor por defecto. Sigue el flujo normal del HTML. |
| **`relative`** | Se mueve respecto a su posición original. Se usa como **punto de referencia** (ancla) para hijos con posición absoluta. |
| **`absolute`** | Se posiciona respecto al ancestro más cercano con `position: relative`. Sale del flujo normal y no ocupa espacio. |
| **`fixed`** | Queda anclado a la pantalla (viewport). No se mueve aunque hagas scroll (ej. botones de chat). |
| **`sticky`** | Se queda "pegado" en una posición relativa mientras su contenedor sea visible en pantalla. |



---

## 3. Z-Index y Contexto de Apilamiento <a name="z-index"></a>

El `z-index` define qué elemento se muestra "encima" de otro en el eje Z (profundidad). 

> ⚠️ **Regla de oro:** Para que un `z-index` funcione, el elemento **debe** tener una propiedad `position` distinta a `static` (usualmente `relative` en el padre).

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

## 4. Flexbox: Diseño Unidimensional <a name="flexbox"></a>

Flexbox está diseñado para organizar elementos en un solo eje (ya sea una fila o una columna). Se activa aplicando `display: flex;` al contenedor padre.



### 4.1 Propiedades del Contenedor (Padre)

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

### 4.2 Propiedades de los Hijos (Items)

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