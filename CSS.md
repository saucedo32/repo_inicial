# 🌐 Guía de Referencia Rápida: CSS Inicial

Esta guía está diseñada para proporcionar una base amplia y rápida sobre las hojas de estilo en cascada. 
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
| **Etiqueta `<style>` (Interno)** | Se coloca dentro del `<head>` del HTML. | `<style> h1 { color: red; } </style>` |
| **Archivo externo (`.css`)** | Se vincula un archivo separado mediante `<link>`. | `<link rel="stylesheet" href="estilos.css">` |

---




## 2. Titulo


---


## 2. Titulo


---


## 2. Titulo


---


## 2. Titulo


---


## 2. Titulo



---

## 2. Titulo


---


2. 


3. Sintaxis y Selectores
La estructura básica de CSS consiste en un Selector, una Propiedad y un Valor.

selector {
  propiedad: valor;
}

Tabla de Selectores Básicos
Selector,Descripción,Ejemplo
Universal,Selecciona todos los elementos del documento.,* { margin: 0; }
De Elemento,Selecciona todas las etiquetas del tipo indicado.,p { color: grey; }
De Clase (.),Selecciona elementos con el atributo class.,.mi-boton { cursor: pointer; }
De ID (#),Selecciona el elemento único con ese id.,#main-header { padding: 20px; }

4. Unidades y Colores
Unidades de Medida
px: Píxeles (unidades fijas en pantalla). Absoluta.
%: Porcentaje relativo al elemento padre. Relativa.
em: Relativo al tamaño de fuente del elemento. Relativa.
rem: Relativo al tamaño de fuente de la raíz (<html>). Relativa.
vh / vw: Relativo al 1% del alto o ancho de la ventana. Relativa.

Nombre,#HEX,RGB / RGBA,HSL
red,#FF0000,"rgb(255, 0, 0)","hsl(0, 100%, 50%)"
blue,#0000FF,"rgba(0, 0, 255, 0.5)","hsl(240, 100%, 50%)"


5. Especificidad y Herencia
Especificidad
Es el sistema que usa el navegador para decidir qué regla se aplica cuando hay conflictos. Se calcula por "puntos":

Estilo en línea: 1000 puntos.
ID (#): 100 puntos.
Clases, atributos y pseudoclases: 10 puntos.
Elementos y pseudoelementos: 1 punto.

Nota: El selector universal (*) tiene 0 puntos. Si hay empate, gana la regla que esté escrita más abajo en el archivo.

Herencia
Algunas propiedades (como color o font-family) se transmiten de padres a hijos automáticamente. Otras (como border o margin) no se heredan.

6. Propiedades Comunes
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


7. El Modelo de Caja (Box Model)
Todos los elementos HTML son cajas rectangulares.
Propiedad,Descripción,Valores frecuentes
Content,"El contenido real (texto, imagen).",Ancho y alto definido.
Padding,Espacio interno entre contenido y borde.,"10px, 1em 2em"
Border,Línea que rodea el padding y contenido.,1px solid black
Margin,Espacio externo fuera del borde.,"auto, 20px"


8. Propiedades de Tamaño
Propiedad,Descripción,Valor por defecto,Valores frecuentes
width / height,Ancho y alto fijo.,auto,"px, %, vh, vw"
min-width,El elemento no será más pequeño que esto.,0,300px
max-width,El elemento no crecerá más de esto.,none,"100%, 1200px"













