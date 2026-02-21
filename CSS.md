# 🌐 Guía de Referencia Rápida: CSS Inicial

Esta guía está diseñada para proporcionar una base amplia y rápida sobre las hojas de estilo en cascada. <br>
Para una consulta profunda y técnica, siempre es recomendable visitar la documentación oficial.

> 📚 **Documentación recomendada:** Para profundizar en cada propiedad y ver ejemplos interactivos, te recomendamos visitar:
>* **[MDN Web Docs - CSS](https://developer.mozilla.org/es/docs/Web/CSS)**: La referencia técnica más completa y actualizada mantenida por la comunidad de Mozilla.
>* **[W3Schools - Tutorial CSS](https://www.w3schools.com/css/)**: Ideal para aprendizaje rápido con ejemplos interactivos y editores en vivo.

---

## 🔍 Índice de Contenidos
1. [¿Qué es CSS?](#1-qué-es-css)
2. [¿Cómo podemos incluir CSS en nuestro HTML?](#2-cómo-podemos-incluir-css-en-nuestro-html)
3. [Sintaxis básica CSS](#3-sintaxis-básica-css)
4. [Tabla de Selectores CSS](#4-tabla-de-selectores-css)
5. [Especificidad](#5-especificidad)
6. [Herencia](#6-herencia)
7. [Unidades de medida y Colores](#7-unidades-de-medida-y-colores)
8. [El Modelo de la Caja (Box Model)](#8-el-modelo-de-la-caja-box-model)
9. [Propiedades más usadas](#9-propiedades-más-usadas)
   - [Color y Fondo](#color-y-fondo)
   - [Tipografía y Texto](#tipografía-y-texto)
   - [Tamaño](#tamaño)
   - [Visualización y Visibilidad](#visualización-y-visibilidad)
   - [Modelo de Caja (Espaciado y Cálculo)](#modelo-de-caja-espaciado-y-cálculo)
   - [Bordes y Contornos](#bordes-y-contornos)
   - [Control de Desbordamiento](#control-de-desbordamiento-overflow)

---

## 1. ¿Qué es CSS?
CSS (**Cascading Style Sheets**) es el lenguaje que utilizamos para definir el aspecto y la presentación de un documento HTML. Mientras que el HTML es el "esqueleto" (estructura), el CSS es la "piel" (diseño, tamaños, colores, fuentes).

---

## 2. ¿Cómo podemos incluir CSS en nuestro HTML?
Existen tres formas de incluir CSS en nuestro proyecto, cada una con un nivel de prioridad y orden distinto:

| Método | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **Atributo `style` (Inline)** | Se escribe directamente en la etiqueta HTML. | `<h1 style="color: red;">Hola</h1>` |
| **Etiqueta `<style>` (Interno en HTML)** | Se coloca dentro del `<head>` del HTML. | `<style> h1 { color: red; } </style>` |
| **Archivo externo (`.css`)** | Se vincula dentro del `<head>` un archivo separado mediante la etiqueta `<link>`. | `<link rel="stylesheet" href="estilos.css">` |

---


## 3. Sintaxis básica CSS

La estructura básica de CSS consiste en un **SELECTOR**, una **PROPIEDAD** y un **VALOR**.

### Anatomía de una regla CSS
> **Selector** {  
> &nbsp;&nbsp; **propiedad**: **valor**;  
> }

* **Selector:** Indica el elemento HTML al que se le aplicará el estilo.
* **Propiedad:** El aspecto que queremos cambiar (color, tamaño, margen).
* **Valor:** El ajuste específico que asignamos a esa propiedad.


---

## 4. Tabla de Selectores CSS
Los selectores permiten aplicar estilos con precisión, desde afectar a todo el documento hasta a un solo elemento basado en su relación con otros.

| Selector | Nombre / Descripción | Ejemplo de uso |
| :--- | :--- | :--- |
| **`*`** | **Universal:** Selecciona absolutamente todos los elementos. | `* { box-sizing: border-box; }` |
| **`tag`** | **De Elemento:** Selecciona todas las etiquetas de ese tipo. | `p { line-height: 1.6; }` |
| **`.clase`** | **De Clase:** Selecciona elementos con ese atributo `class`. | `.destacado { color: gold; }` |
| **`#id`** | **De ID:** Selecciona el elemento único con ese `id`. | `#main-nav { background: #333; }` |
| **`s1 s2`** | **Descendiente:** Selecciona `s2` si está dentro de `s1`. | `div p { font-style: italic; }` |
| **`.c1.c2`** | **Multiclase:** Elementos que tienen AMBAS clases. | `.btn.sucess { color: green; }` |
| **`s1.c1`** | **Elemento con Clase:** El elemento `s1` que tenga la clase `c1`. | `img.avatar { border-radius: 50%; }` |
| **`s1, s2`** | **Agrupación:** Aplica el mismo estilo a varios selectores. | `h1, h2, h3 { margin-bottom: 10px; }` |
| **`s1 > s2`** | **Hijo Directo:** `s2` debe ser hijo inmediato de `s1`. | `ul > li { list-style: none; }` |
| **`s1 + s2`** | **Hermano Adyacente:** El elemento `s2` que sigue justo a `s1`. | `h1 + p { margin-top: 0; }` |

### Notas de Aplicación
1. **Combinadores:** Los espacios (` `) y los símbolos (`>`, `+`) cambian el alcance. Un espacio busca en **toda la profundidad**, mientras que `>` solo busca en el **primer nivel**.
2. **Eficiencia:** Evita encadenar demasiados selectores (ej. `body div section ul li a`). Cuanto más corto sea el selector, más rápido lo procesará el navegador.
3. **Prioridad:** Recuerda que un `id` siempre le ganará a una `clase`, y una `clase` le ganará a un `elemento`.

---


## 5. Especificidad
Es el sistema que usa el navegador para decidir qué regla se aplica cuando hay conflictos (varias reglas apuntando al mismo elemento).

> **Puntuación de Especificidad:**
> * **Estilo en línea:** 1000 puntos.
> * **ID (`#`):** 100 puntos.
> * **Clases, atributos y pseudoclases:** 10 puntos.
> * **Elementos y pseudoelementos:** 1 punto.
> * **Selector universal (`*`):** 0 puntos.

**Nota:** Si hay un empate en puntos, prevalece la regla que esté escrita **más abajo** en el archivo CSS.

---

## 6. Herencia
No todas las propiedades se comportan igual al aplicarse a un elemento padre:

* **Propiedades heredadas:** Se transmiten automáticamente a los hijos (ej: `color`, `font-family`, `line-height`).
* **Propiedades NO heredadas:** Deben definirse específicamente para cada elemento (ej: `border`, `margin`, `padding`, `background`).

---
## 7. Unidades de medida y Colores
El manejo de medidas y colores es fundamental para lograr diseños consistentes y accesibles.

### Unidades de medida
| Unidad | Tipo | Descripción | Ejemplo |
| :--- | :--- | :--- | :--- |
| **`px`** | Absoluta | Píxeles fijos en pantalla. | `font-size: 16px;` |
| **`%`** | Relativa | Porcentaje respecto al elemento padre. | `width: 50%;` |
| **`em`** | Relativa | Relativo al tamaño de fuente del elemento. | `margin: 2em;` |
| **`rem`** | Relativa | Relativo al tamaño de fuente raíz (`<html>`). | `padding: 1.5rem;` |
| **`vh` / `vw`** | Relativa | 1% del alto (`vh`) o ancho (`vw`) de la ventana. | `height: 100vh;` |

### Formatos de Color
Los colores en CSS pueden definirse de múltiples formas dependiendo de la precisión o la transparencia que necesites para el diseño.

| Nombre | Hexadecimal | RGB / RGBA | HSL |
| :--- | :--- | :--- | :--- |
| **`red`** 🔴 | `#FF0000` | `rgb(255, 0, 0)` | `hsl(0, 100%, 50%)` |
| **`blue`** 🔵 | `#0000FF` | `rgba(0, 0, 255, 0.5)` | `hsl(240, 100%, 50%)` |
| **`green`** 🟢 | `#008000` | `rgb(0, 128, 0)` | `hsl(120, 100%, 25%)` |
| **`yellow`** 🟡 | `#FFFF00` | `rgb(255, 255, 0)` | `hsl(60, 100%, 50%)` |
| **`orange`** 🟠 | `#FFA500` | `rgb(255, 165, 0)` | `hsl(39, 100%, 50%)` |
| **`purple`** 🟣 | `#800080` | `rgb(128, 0, 128)` | `hsl(300, 100%, 25%)` |
| **`lightblue`** 🔵 | `#ADD8E6` | `rgb(173, 216, 230)` | `hsl(195, 53%, 79%)` |
| **`black`** ⚫ | `#000000` | `rgb(0, 0, 0)` | `hsl(0, 0%, 0%)` |
| **`white`** ⚪ | `#FFFFFF` | `rgb(255, 255, 255)` | `hsl(0, 0%, 100%)` |


* **Nombres Clave (`Keywords`):** Son palabras predefinidas (como `red` o `lightblue`). Son geniales para prototipos rápidos, pero limitadas a 140 nombres estándar.
* **Hexadecimal (`#HEX`):** El estándar más usado en la web. Representa la mezcla de Rojo, Verde y Azul en código base 16. Es ideal para copiar colores exactos de herramientas como Figma o Photoshop.
* **RGB / RGBA:** Define la intensidad de Rojo, Verde y Azul en valores de **0 a 255**. La versión **RGBA** añade un canal "Alpha" (de 0 a 1) para manejar transparencias.
* **HSL:** Siglas de **Hue** (Tono), **Saturation** (Saturación) y **Lightness** (Luminosidad). Es el formato más intuitivo para humanos, ya que permite aclarar u oscurecer un color simplemente cambiando el porcentaje de brillo.

---


## 8. El Modelo de la Caja (Box Model)
En CSS, cada elemento se considera una caja rectangular. Comprender cómo interactúan sus partes es fundamental para controlar el diseño y el espaciado de una página web.

### Representación Visual
A continuación se muestra cómo se estructuran las capas desde el centro hacia afuera:

```text
 _______________________________________
|                MARGIN                 |  <- Espacio externo (separa de otros elementos)
|    _______________________________    |
|   |            BORDER             |   |  <- Línea de contorno (grosor/estilo)
|   |    _______________________    |   |
|   |   |       PADDING         |   |   |  <- Espacio interno (distancia al borde)
|   |   |    _______________    |   |   |
|   |   |   |               |   |   |   |
|   |   |   |    CONTENT    |   |   |   |  <- El contenido real (texto/imagen)
|   |   |   |_______________|   |   |   |
|   |   |_______________________|   |   |
|   |_______________________________|   |
|_______________________________________|
```


### Desglose de Capas del Box Model
Cada propiedad cumple un rol específico en la estructura y el espaciado del elemento:

| Capa | Descripción | Propiedades CSS |
| :--- | :--- | :--- |
| **Content** | El área donde se renderiza el texto o la imagen. | `width`, `height` |
| **Padding** | Espacio transparente entre el contenido y el borde. | `padding`, `padding-top`, `padding-left`, etc. |
| **Border** | Capa que rodea el padding. Tiene grosor, color y estilo. | `border`, `border-width`, `border-style`, `border-radius` |
| **Margin** | Espacio exterior que separa el elemento de sus vecinos. | `margin`, `margin-bottom`, `margin-right`, `auto` |


### Valores frecuentes en Box Model
| Capa | Descripción | Valores frecuentes |
| :--- | :--- | :--- |
| **Content** | El contenido real (texto o imagen). | Ancho y alto definidos. |
| **Padding** | Espacio interno entre contenido y borde. | `10px`, `1em 2em` |
| **Border** | Línea que rodea el padding y contenido. | `1px solid black` |
| **Margin** | Espacio externo fuera del borde. | `auto`, `20px` |



### Ejemplo Práctico: ¿Por qué usar `border-box`?
Para entender el impacto de este "reset", comparemos cómo se comportan dos cajas con las mismas propiedades bajo distintos modelos:

#### El Escenario
Queremos una caja que mida **300px** de ancho total, con un relleno interno de **20px** y un borde de **5px**.

#### Comparativa de Modelos
| Modelo | Resultado en Pantalla | Cálculo Técnico |
| :--- | :--- | :--- |
| **`content-box`** (Default) | **350px** ⚠️ | 300 (Content) + 40 (Padding L/R) + 10 (Border L/R) |
| **`border-box`** (Reset) | **300px** ✅ | 250 (Content) + 40 (Padding L/R) + 10 (Border L/R) |


### Ejemplo de Código
Si aplicas el reset universal al inicio de tu CSS, garantizas que tus diseños no se "rompan" al añadir padding:

```css
/* 1. RESET UNIVERSAL */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box; /* El ancho definido será el ancho FINAL */
}

/* 2. APLICACIÓN */
.caja-perfecta {
  width: 300px;
  padding: 20px;
  border: 5px solid #333;
  /* Gracias al reset, esta caja medirá exactamente 300px en el navegador */
}
```

---

## 9. Propiedades más usadas

### Color y Fondo
| Propiedad | Descripción | Valor por defecto | Valores frecuentes |
| :--- | :--- | :--- | :--- |
| `color` | Color del texto. | `initial` | Hex, RGB, nombre. |
| `background-color` | Color de fondo. | `transparent` | Hex, RGB, nombre. |
| `background-image` | Imagen de fondo. | `none` | `url('ruta/img.jpg')` |


### Tipografía y Texto
| Propiedad | Descripción | Valor por defecto | Valores frecuentes |
| :--- | :--- | :--- | :--- |
| `text-align` | Alineación horizontal. | `left` | `center`, `right`, `justify` |
| `text-decoration` | Decoración visual. | `none` | `underline`, `line-through` |
| `font-family` | Familia tipográfica. | Varía | `Arial`, `sans-serif` |
| `font-size` | Tamaño de la letra. | `medium` | `16px`, `1.2rem`, `110%` |
| `font-weight` | Grosor de la letra. | `normal` | `bold`, `400`, `700` |

### Tamaño
| Propiedad | Descripción | Valor por defecto | Valores frecuentes |
| :--- | :--- | :--- | :--- |
| `width` / `height` | Ancho y alto fijo. | `auto` | `px`, `%`, `vh`, `vw` |
| `min-width` | Tamaño mínimo garantizado. | `0` | `300px` |
| `max-width` | Límite máximo de crecimiento. | `none` | `100%`, `1200px` |

### Visualización y Visibilidad
Determinan cómo se comporta el elemento en el flujo del documento.

| Propiedad | Descripción | Valor por defecto | Valores frecuentes |
| :--- | :--- | :--- | :--- |
| **`display`** | Define el tipo de caja de renderizado. | `inline` / `block` | `flex`, `grid`, `inline-block`, `none` |
| **`visibility`** | Oculta el elemento pero mantiene su espacio. | `visible` | `hidden` |
| **`opacity`** | Nivel de transparencia del elemento. | `1` | `0` (invisible) hasta `1` (opaco) |
| **`cursor`** | Cambia el aspecto del puntero del mouse. | `auto` | `pointer`, `not-allowed`, `grab` |

### Modelo de Caja (Espaciado y Cálculo)
Propiedades principales que definen el tamaño de la caja.

| Propiedad | Descripción | Valor por defecto | Valores frecuentes |
| :--- | :--- | :--- | :--- |
| **`padding`** | Espacio interno entre el contenido y el borde. | `0` | `10px`, `1rem 2rem`, `5%` |
| **`margin`** | Espacio externo que separa al elemento de otros. | `0` | `20px`, `auto` (para centrar) |
| **`box-sizing`** | Define si el ancho total incluye el padding/borde. | `content-box` | `border-box` (Recomendado) |


### Bordes y Contornos
Controlan el marco, el estilo y la forma de los "recuadros".

| Propiedad | Descripción | Valor por defecto | Valores frecuentes |
| :--- | :--- | :--- | :--- |
| **`border`** | **Shorthand:** Define ancho, estilo y color en una línea. | `none` | `2px solid black` |
| **`border-width`** | Grosor de la línea del borde. | `medium` | `1px`, `4px`, `0.2rem` |
| **`border-style`** | Tipo de línea (Sólida, punteada, etc.). | `none` | `solid`, `dashed`, `dotted`, `double` |
| **`border-color`** | Color de la línea del borde. | `currentcolor` | `red`, `#333`, `transparent` |
| **`border-radius`** | Redondea las esquinas del recuadro. | `0` | `8px`, `50%` (círculos), `20px` |
| **`outline`** | Línea externa que **no** ocupa espacio en el diseño. | `none` | `3px solid blue` |

### Control de Desbordamiento (`overflow`)
Controla qué sucede cuando el contenido supera el tamaño del contenedor:
* **`visible`**: El contenido sobresale (por defecto).
* **`hidden`**: Se recorta lo que sobra.
* **`scroll`**: Añade barras de desplazamiento permanentemente.
* **`auto`**: Añade barras solo si el contenido se desborda.








