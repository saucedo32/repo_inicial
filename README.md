# 📑 HTML5 Cheatsheet: Guía de Referencia Rápida

Esta guía sirve como un resumen práctico de los fundamentos de HTML5, ideal para consultas rápidas y para entender la jerarquía y estructura de la web.

> 📚 **Documentación de interés:** Para profundizar en cada etiqueta y ver ejemplos interactivos, te recomendamos visitar [W3Schools - HTML Tutorial](https://www.w3schools.com/html/).

---

## 1. ¿Qué es HTML?
**HTML** (*HyperText Markup Language*) es el lenguaje de marcado estándar para la creación de páginas web. No es un lenguaje de programación, su función es definir la **estructura** y el **contenido** (texto, imágenes, enlaces) de un documento mediante etiquetas.

---

## 2. Estructura básica
Todo documento HTML5 debe contar con la siguiente anatomía mínima:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Primera Página</title>
</head>
<body>
    <h1>¡Hola Mundo!</h1>
    <p>Este es el inicio de mi documento.</p>
</body>
</html>
```

---

## 3. ¿Qué son los elementos o etiquetas HTML?
Un elemento es la unidad básica de HTML. La mayoría se componen de una etiqueta de apertura, contenido y una etiqueta de cierre.

**Anatomía de un elemento:**
`<etiqueta atributo="valor"> Contenido </etiqueta>`



| Elemento | Descripción |
| :--- | :--- |
| `<h1>` a `<h6>` | Encabezados de mayor a menor importancia. |
| `<p>` | Define un párrafo de texto. |
| `<a>` | Define un hipervínculo (requiere atributo `href`). |
| `<ul>` / `<ol>` | Listas desordenadas (puntos) u ordenadas (números). |
| `<li>` | Ítem individual dentro de una lista. |
| `<img>` | Inserta una imagen (Etiqueta vacía: no requiere cierre). |

---

## 4. Comportamiento: Bloque vs. Línea
Es vital entender cómo se posicionan los elementos en el navegador:



* **Bloque (`Block`):** Ocupan todo el ancho disponible y siempre inician en una nueva línea. 
    * *Ejemplos:* `<div>`, `<h1>`, `<p>`, `<section>`.
* **Línea (`Inline`):** Solo ocupan el ancho de su contenido y no fuerzan un salto de línea (se mantienen uno al lado del otro). 
    * *Ejemplos:* `<span>`, `<a>`, `<strong>`, `<img>`.

---

## 5. Atributos de elementos HTML
Los atributos proporcionan información adicional o modifican el comportamiento de un elemento. Se escriben siempre en la **etiqueta de apertura**.

### Atributos Globales (Para casi todos los elementos)
* **`id`**: Identificador único en toda la página (ideal para JS o anclas).
* **`class`**: Identificador para aplicar estilos CSS (puede repetirse en varios elementos).
* **`style`**: Define estilos CSS directos (no recomendado para proyectos grandes).
* **`title`**: Información extra que aparece al pasar el cursor (tooltip).

### Atributos Particulares
* **`href`**: Destino de un enlace (usado en `<a>`).
* **`src`**: Ruta del archivo o recurso (usado en `<img>`, `<video>`, `<script>`).
* **`alt`**: Texto descriptivo para accesibilidad (usado en `<img>`).

---

## 6. Elementos estructurales
Sirven para organizar el documento sin aportar un significado específico al contenido ("cajas" de organización).

| Elemento | Descripción |
| :--- | :--- |
| `<div>` | Contenedor de bloque genérico. |
| `<span>` | Contenedor de línea genérico (para fragmentos de texto). |

---

## 7. Elementos semánticos
Le comunican al navegador y a los buscadores **qué función cumple** cada parte del sitio, mejorando drásticamente el SEO y la accesibilidad.



| Elemento | Descripción |
| :--- | :--- |
| `<header>` | Cabecera del sitio o de una sección. |
| `<nav>` | Contenedor de enlaces de navegación (menús). |
| `<main>` | Contenido principal y único de la página. |
| `<section>` | Agrupación temática de contenido. |
| `<article>` | Contenido independiente (noticia, post de blog). |
| `<aside>` | Contenido relacionado de forma indirecta (barras laterales). |
| `<footer>` | Pie de página con información legal o de contacto. |

---

## 8. Etiquetas de contenido
| Elemento | Descripción |
| :--- | :--- |
| `<strong>` | Indica importancia fuerte (se visualiza en negrita). |
| `<em>` | Indica énfasis (se visualiza en cursiva). |
| `<br>` | Salto de línea manual. |
| `<hr>` | Línea horizontal divisoria. |

---

## 9. Etiquetas para creación de formularios
| Elemento | Descripción |
| :--- | :--- |
| `<form>` | Contenedor principal para envío de datos. |
| `<label>` | Texto vinculado a un campo (mejora la accesibilidad). |
| `<input>` | Campo de entrada de datos (el más versátil). |
| `<textarea>` | Cuadro de texto para mensajes largos. |
| `<select>` | Menú desplegable de opciones. |
| `<button>` | Botón para ejecutar acciones o enviar. |

---

## 10. Atributos de la etiqueta `<input>`
El comportamiento del `<input>` cambia según su atributo `type`:

* **`type="text"`**: Texto corto.
* **`type="password"`**: Caracteres ocultos.
* **`type="email"`**: Valida estructura de correo electrónico.
* **`type="checkbox"`**: Casilla de selección múltiple.
* **`type="radio"`**: Opción de selección única entre un grupo.
* **Extras:** `placeholder` (pista visual), `required` (campo obligatorio), `name` (nombre del dato para el servidor).

---

## 11. Tablas de contenido
| Elemento | Descripción |
| :--- | :--- |
| `<table>` | Contenedor principal de la tabla. |
| `<thead>` | Grupo de encabezados de columna. |
| `<tbody>` | Cuerpo que contiene los datos principales. |
| `<tr>` | Fila de la tabla (*table row*). |
| `<th>` | Celda de encabezado (título de columna/fila). |
| `<td>` | Celda de datos estándar. |

---

## 12. Contenido incrustado y Metaetiquetas

### Contenido incrustado
* **`<iframe>`**: Inserta otro documento o sitio web (ej. Google Maps).
* **`<video>` / `<audio>`**: Reproduce multimedia nativa. Es recomendable usar el atributo `controls`.

### Metaetiquetas (Dentro de `<head>`)
* **`<meta charset="UTF-8">`**: Codificación necesaria para tildes y letras "ñ".
* **`<meta name="viewport" content="...">`**: Clave para que el diseño sea responsive (se adapte a móviles).
* **`<meta name="description" content="...">`**: Resumen del sitio que aparece en Google.

---

## 13. Accesibilidad Web (A11y)
* **Jerarquía:** Usar un solo `<h1>` por página y seguir un orden lógico (`h2`, luego `h3`).
* **Imágenes:** Usar siempre el atributo `alt` descriptivo para lectores de pantalla.
* **Vinculación:** Usar el atributo `for` en el `<label>` coincidiendo con el `id` del `<input>`.
* **Semántica:** Priorizar siempre el uso de etiquetas semánticas sobre los simples `<div>`.




