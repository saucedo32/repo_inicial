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







