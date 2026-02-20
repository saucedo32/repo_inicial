# 🌐 Guía de Referencia Rápida: CSS Inicial

Esta guía está diseñada para proporcionar una base amplia y rápida sobre las hojas de estilo en cascada. <br>
Para una consulta profunda y técnica, siempre es recomendable visitar la documentación oficial.

> 📚 **Documentación recomendada:** Para profundizar en cada propiedad y ver ejemplos interactivos, te recomendamos visitar:
* **[MDN Web Docs - CSS](https://developer.mozilla.org/es/docs/Web/CSS)**: La referencia técnica más completa y actualizada mantenida por la comunidad de Mozilla.
* **[W3Schools - Tutorial CSS](https://www.w3schools.com/css/)**: Ideal para aprendizaje rápido con ejemplos interactivos y editores en vivo.

---

## 1. ¿Qué es CSS?
CSS (**Cascading Style Sheets**) es el lenguaje que utilizamos para definir el aspecto y la presentación de un documento HTML. Mientras que el HTML es el "esqueleto" (estructura), el CSS es la "piel" (diseño, tamaños, colores, fuentes).

---

## 2. Métodos de Implementación
Existen tres formas de incluir CSS en nuestro proyecto, cada una con un nivel de prioridad y orden distinto:

| Método | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **Atributo `style` (Inline)** | Se escribe directamente en la etiqueta HTML. | `<h1 style="color: red;">Hola</h1>` |
| **Etiqueta `<style>` (Interno en HTML)** | Se coloca dentro del `<head>` del HTML. | `<style> h1 { color: red; } </style>` |
| **Archivo externo (`.css`)** | Se vincula un archivo separado mediante `<link>`. | `<link rel="stylesheet" href="estilos.css">` |

---




## 3. Sintaxis y Selectores
La estructura básica de CSS consiste en un Selector, una Propiedad y un Valor.

### Anatomía de una regla CSS
> **Selector** {  
> &nbsp;&nbsp; **propiedad**: **valor**;  
> }

* **Selector:** Indica el elemento HTML al que se le aplicará el estilo.
* **Propiedad:** El aspecto que queremos cambiar (color, tamaño, margen).
* **Valor:** El ajuste específico que asignamos a esa propiedad.


### Selectores Básicos
Los selectores permiten apuntar a los elementos con diferentes niveles de precisión:

| Selector | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **Universal (`*`)** | Selecciona **todos** los elementos del documento. | `* { margin: 0; }` |
| **De Elemento** | Selecciona todas las etiquetas del tipo indicado. | `p { color: gray; }` |
| **De Clase (`.`)** | Selecciona elementos con un atributo `class` específico. | `.mi-boton { cursor: pointer; }` |
| **De ID (`#`)** | Selecciona el elemento **único** que tenga ese `id`. | `#main-header { padding: 20px; }` |


---

## 4. Unidades y Colores
El manejo de medidas y colores es fundamental para lograr diseños consistentes y accesibles.

### Unidades de Medida
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

## 7. Propiedades Comunes

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

### Control de Desbordamiento (`overflow`)
Controla qué sucede cuando el contenido supera el tamaño del contenedor:
* **`visible`**: El contenido sobresale (por defecto).
* **`hidden`**: Se recorta lo que sobra.
* **`scroll`**: Añade barras de desplazamiento permanentemente.
* **`auto`**: Añade barras solo si el contenido se desborda.

---

## 8. El Modelo de Caja (Box Model)

Todos los elementos HTML se visualizan como cajas rectangulares compuestas por capas:

| Capa | Descripción | Valores frecuentes |
| :--- | :--- | :--- |
| **Content** | El contenido real (texto o imagen). | Ancho y alto definidos. |
| **Padding** | Espacio interno entre contenido y borde. | `10px`, `1em 2em` |
| **Border** | Línea que rodea el padding y contenido. | `1px solid black` |
| **Margin** | Espacio externo fuera del borde. | `auto`, `20px` |

---

## 9. Propiedades de Tamaño
| Propiedad | Descripción | Valor por defecto | Valores frecuentes |
| :--- | :--- | :--- | :--- |
| `width` / `height` | Ancho y alto fijo. | `auto` | `px`, `%`, `vh`, `vw` |
| `min-width` | Tamaño mínimo garantizado. | `0` | `300px` |
| `max-width` | Límite máximo de crecimiento. | `none` | `100%`, `1200px` |

---





---
---
---
---
---
---
---
---
---

## 4. Unidades y Colores

Unidades de Medida
px: Píxeles (unidades fijas en pantalla). Absoluta.
%: Porcentaje relativo al elemento padre. Relativa.
em: Relativo al tamaño de fuente del elemento. Relativa.
rem: Relativo al tamaño de fuente de la raíz (<html>). Relativa.
vh / vw: Relativo al 1% del alto o ancho de la ventana. Relativa.

Nombre,#HEX,RGB / RGBA,HSL
red,#FF0000,"rgb(255, 0, 0)","hsl(0, 100%, 50%)"
blue,#0000FF,"rgba(0, 0, 255, 0.5)","hsl(240, 100%, 50%)"


---


## 5. Especificidad 
Especificidad
Es el sistema que usa el navegador para decidir qué regla se aplica cuando hay conflictos. Se calcula por "puntos":

Estilo en línea: 1000 puntos.
ID (#): 100 puntos.
Clases, atributos y pseudoclases: 10 puntos.
Elementos y pseudoelementos: 1 punto.

Nota: El selector universal (*) tiene 0 puntos. Si hay empate, gana la regla que esté escrita más abajo en el archivo.


---


## 6. Herencia
Herencia
Algunas propiedades (como color o font-family) se transmiten de padres a hijos automáticamente. Otras (como border o margin) no se heredan.

---


## 7. Propiedades Comunes
Color y Fondo

Propiedad,Descripción,Valor por defecto,Valores frecuentes
color,Color del texto.,initial,"hex, rgb, name"
background-color,Color de fondo.,transparent,"hex, rgb, name"
background-image,Imagen de fondo.,none,url('ruta/img.jpg')

Propiedad,Descripción,Valor por defecto,Valores frecuentes
text-align,Alineación horizontal.,left,"center, right, justify"
text-decoration,Decoración del texto.,none,"underline, line-through"
font-family,Familia tipográfica.,Varia,"Arial, sans-serif"
font-size,Tamaño de la letra.,medium,"16px, 1.2rem"
font-weight,Grosor de la letra.,normal,"bold, 400, 700"

Listas y Tablas
list-style-type: Cambia el icono de la lista (none, square, circle).
border-collapse: Une los bordes de la tabla (collapse, separate).

Pseudoclases
:hover: Se activa cuando el usuario pasa el cursor sobre el elemento.

overflow: Controla qué pasa cuando el contenido es más grande que su contenedor.
visible: El contenido se sale.
hidden: Se recorta lo que sobra.
scroll: Añade barras de desplazamiento siempre.
auto: Añade barras solo si es necesario.



---

## 8. El Modelo de Caja (Box Model)
Todos los elementos HTML son cajas rectangulares.
Propiedad,Descripción,Valores frecuentes
Content,"El contenido real (texto, imagen).",Ancho y alto definido.
Padding,Espacio interno entre contenido y borde.,"10px, 1em 2em"
Border,Línea que rodea el padding y contenido.,1px solid black
Margin,Espacio externo fuera del borde.,"auto, 20px"


---

## 9. Propiedades de Tamaño
Propiedad,Descripción,Valor por defecto,Valores frecuentes
width / height,Ancho y alto fijo.,auto,"px, %, vh, vw"
min-width,El elemento no será más pequeño que esto.,0,300px
max-width,El elemento no crecerá más de esto.,none,"100%, 1200px"


---

## 9. 


---

## 9. 


---

## 9. 


---

## 9. 


---



2. 


3. 

4. 


5. 



6. 


7. 


8. 













