# 🌐 Guía de Referencia Rápida: JavaScript
Esta guía resume los fundamentos de JavaScript desde la introducción básica hasta el consumo de APIs, orientada a la resolución del Trabajo Práctico Final.

> 📚 **Documentación recomendada:**
> * **[MDN Web Docs - JavaScript](https://developer.mozilla.org/es/docs/Web/JavaScript)**
> * **[W3Schools - JS Tutorial](https://www.w3schools.com/js/)**

Se puede usar la siguiente web para hacer pruebas en línea:
>🛠️ **Herramienta para pruebas**
>Se puede usar la siguiente web para hacer pruebas en línea, ver cambios en tiempo real y compartir código:
> * **[codi.link - Editor de código online](https://codi.link/)**

---

## 🔍 Índice de Contenidos
1. [Introducción, Variables y Tipos de Datos](#intro-js)
   * [Implementación de JavaScript en HTML](#implementación-de-javascript-en-html)
   * [Declaración de Variables en JavaScript](#declaración-de-variables-en-javascript)
   * [Tipos de datos primitivos en JavaScript](#tipos-de-datos-primitivos-en-javascript)
2. [Operadores Básicos en JavaScript](#operadores-js)
   * [1. Operadores Aritméticos y de Asignación](#1-operadores-aritméticos-y-de-asignación)
   * [2. Operadores de Comparación](#2-operadores-de-comparación-devuelven-booleanos)
   * [3. Operadores Lógicos](#3-operadores-lógicos)
3. [Flujos de Control en JS](#flujo-control)
   * [Estructuras Condicionales (if / else)](#estructuras-condicionales-if--else)
   * [Ciclos (Bucles) for y while](#ciclos-bucles-for-y-while)
4. [Funciones en JS](#funciones)
   * [Anatomía de una Función](#anatomía-de-una-función)
5. [Manipulación del DOM con JS](#DOM)
   * [Selección y Propiedades](#manipulación-del-dom-con-js)
   * [Gestión de Eventos en JavaScript](#gestión-de-eventos-en-javascript)
6. [Consumo de APIs (JSON y fetch)](#APIs-JSON)
   * [¿Qué es JSON?](#qué-es-json)
   * [Conceptos Clave de fetch](#fetch)
   * [Ejemplo Práctico: Obtener el Clima](#ejemplo-práctico-obtener-el-clima)


---


## Introducción, Variables y Tipos de Datos <a name="intro-js"></a>
JavaScript es el lenguaje que permite dar interactividad a nuestras páginas web. Se ejecuta del lado del cliente (navegador).

### Implementación de JavaScript en HTML

| Método | Descripción | Ubicación recomendada |
| :--- | :--- | :--- |
| **Externo** | Archivo .js separado (Recomendado). | `<script src="script.js"></script>` antes de cerrar </body>. |
| **Interno** | Código dentro de etiquetas <script>. | Al final del <body>. |
| **En línea** | Atributos HTML (ej: onclick). | Directo en la etiqueta (No recomendado para lógica compleja). |


### Declaración de Variables en JavaScript

| Palabra Clave | Descripción | Recomendación |
| :--- | :--- | :--- |
| **`let`** | Permite declarar variables que pueden cambiar su valor (ámbito de bloque). | Uso estándar para valores mutables. |
| **`const`** | Para valores que permanecerán constantes durante la ejecución. | Preferido por defecto para evitar errores. |
| **`var`** | Forma antigua de declarar variables. | **Evitar su uso** (problemas de hoisting/ámbito). |


### Tipos de datos primitivos en JavaScript

| Tipo | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **`Number`** | Números enteros o decimales. | `let edad = 25;` |
| **`String`** | Cadenas de texto (entre comillas). | `let nombre = "Juan";` |
| **`Boolean`** | Valores lógicos: verdadero o falso. | `let esAdmin = true;` |
| **`Null`** | Representa la ausencia intencional de valor. | `let dato = null;` |
| **`Undefined`** | Variable declarada pero sin valor asignado. | `let x;` |

## Operadores Básicos en JavaScript <a name="operadores-js"></a>

### 1. Operadores Aritméticos y de Asignación

| Operador | Acción | Ejemplo | Resultado (si x=10) |
| :--- | :--- | :--- | :--- |
| **`+`** | Suma | `x + 5` | 15 |
| **`-`** | Resta | `x - 3` | 7 |
| **`*`** | Multiplicación | `x * 2` | 20 |
| **`/`** | División | `x / 2` | 5 |
| **`%`** | Módulo (Resto) | `x % 3` | 1 |
| **`++`** | Incremento (+1) | `x++` | 11 |
| **`+=`** | Suma y asigna | `x += 5` | 15 |

### 2. Operadores de Comparación (Devuelven Booleanos)

| Operador | Significado | Ejemplo (x=10) | Resultado |
| :--- | :--- | :--- | :--- |
| **`==`** | Igualdad de valor | `x == "10"` | true |
| **`===`** | Igualdad estricta (y tipo) | `x === "10"` | false |
| **`!=`** | Distinto valor | `x != 8` | true |
| **`> / <`** | Mayor que / Menor que | `x > 20` | false |
| **`>= / <=`** | Mayor o igual / Menor o igual | `x >= 10` | true |

### 3. Operadores Lógicos

| Operador | Nombre | Descripción | Ejemplo |
| :--- | :--- | :--- | :--- |
| **`&&`** | AND | true si AMBAS condiciones se cumplen. | `(x > 5 && x < 15)` |
| **`||`** | OR | true si AL MENOS UNA condición se cumple. | `(x > 20 || x == 10)` |
| **`!`** | NOT | Invierte el valor (true -> false). | `!(x == 10)` |




## Flujos de Control en JS <a name="flujo-control"></a>

### Estructuras Condicionales (if / else)
Permiten ejecutar código solo si se cumple una condición determinada.

| Operador | Significado | Operador Lógico | Significado |
| :--- | :--- | :--- | :--- |
| **`==`** | Igualdad de valor | **`&&`** | AND (Y) |
| **`===`** | Igualdad estricta (valor y tipo) | **`||`** | OR (O) |
| **`!=`** | Distinto | **`!`** | NOT (Negación) |
| **`> / <`** | Mayor o menor que | | |

**Ejemplo Condicional `if - else`**
```javascript
let llueve = true;

if (llueve) {
    console.log("Llevar paraguas");
} else {
    console.log("No es necesario el paraguas");
}
```

**Ejemplo Condicional `if - else if - else`**
```javascript
let nota = 8;
if (nota >= 9) {
    console.log("Excelente");
} else if (nota >= 7) {
    console.log("Aprobado");
} else {
    console.log("Desaprobado");
}
```

---

### Ciclos (Bucles) for y while
Repiten un bloque de código mientras se cumpla una condición específica.

| Tipo de Ciclo | Descripción | Ejemplo de Uso |
| :--- | :--- | :--- |
| **`while`** | Se ejecuta mientras la condición sea verdadera. | `while (condicion) { ... }` |
| **`for`** | Ideal cuando sabemos cuántas veces repetir. | `for (let i = 0; i < 5; i++) { ... }` |

**Ejemplo de ciclo for:**
```javascript
for (let i = 0; i < 5; i++) {
    console.log("Número: " + i);
}
```

**Ejemplo de ciclo while:**
```javascript
let contador = 0;

while (contador < 3) {
    console.log("Contando: " + contador);
    contador++; // Importante para evitar bucles infinitos
}
```


## Funciones en JS <a name="funciones"></a>
Son bloques de código reutilizables que realizan una tarea específica y pueden devolver un resultado.


**Anatomía de una Función**
| Componente | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **Declaración** | Define la función y sus parámetros. | `function saludar(nombre) { ... }` |
| **Ejecución** | Llama a la función para que realice su tarea. | `let mensaje = saludar("Estudiante");` |


**Ejemplo de declaración de función**
```js
// Declaración de función
function saludar(nombre) {
    return "Hola " + nombre;
}

// Ejecución
let mensaje = saludar("Estudiante");
console.log(mensaje);
```



## Manipulación del DOM con JS <a name="DOM"></a>
El DOM (Document Object Model) es la estructura jerárquica de nuestro HTML vista desde JavaScript.

| Acción | Método / Propiedad | Ejemplo |
| :--- | :--- | :--- |
| **Seleccionar por ID** | `document.getElementById('id')` | `const btn = document.getElementById('enviar');` |
| **Seleccionar general** | `document.querySelector('.clase')` | `const titulo = document.querySelector('h1');` |
| **Cambiar texto** | `.innerText` | `el.innerText = "Nuevo texto";` |
| **Cambiar HTML** | `.innerHTML` | `el.innerHTML = "<b>Negrita</b>";` |
| **Leer input** | `.value` | `let correo = inputEmail.value;` |


### Gestión de Eventos en JavaScript
Los eventos permiten "escuchar" acciones del usuario (clics, teclas presionadas, desplazamientos) y ejecutar código en respuesta.

| Componente | Función | Ejemplo |
| :--- | :--- | :--- |
| **Elemento** | El objeto del DOM que recibirá el evento. | `const boton = document.querySelector("#miBoton");` |
| **Listener** | El método que "escucha" la acción. | `boton.addEventListener("click", ...);` |
| **Callback** | La función que se ejecuta al ocurrir el evento. | `function() { alert("¡Hiciste clic!"); }` |


**Ejemplo con un botón:**
```javascript
// 1. Seleccionamos el elemento
const boton = document.querySelector("#miBoton");

// 2. Escuchamos el evento 'click' y definimos la acción
boton.addEventListener("click", function() {
    alert("¡Hiciste clic!");
});
```



## Consumo de APIs (JSON y fetch) <a name="APIs-JSON"></a>

Para sumar datos externos (como el precio del dólar en el TP Final), usamos APIs.

### ¿Qué es JSON?
Es un formato de intercambio de datos ligero, basado en texto, fácil de leer para humanos y máquinas.

| Concepto | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **JSON** | JavaScript Object Notation | `{"clave": "valor"}` |
| **Objeto** | Estructura de datos en JS | `{ nombre: "Dólar" }` |

**Ejemplo de estructura JSON:**
```json
{
  "nombre": "Dólar Blue",
  "valor": 1200
}
```

### fetch
El método fetch() nos permite realizar peticiones HTTP a servidores externos para obtener o enviar datos de forma asíncrona.<br>
Para integrar datos externos en tiempo real (como el clima o cotizaciones) utilizamos el método fetch.

**Conceptos Clave de fetch**
| Componente     | Función                                      | Ejemplo / Código                     |
| :------------- | :------------------------------------------- | :----------------------------------- |
| **URL (Endpt)** | La dirección de la API a la que llamamos.    | 'https://api.weather.com/v1/...'     |
| **Promise** | Objeto que representa un valor futuro.       | fetch(url) -> devuelve una promesa.  |
| **.then()** | Maneja la respuesta cuando llega con éxito.  | .then(response => response.json())   |
| **.catch()** | Captura errores (ej: caída de internet).     | .catch(error => console.log(error))  |
| **JSON** | Formato en que la API entrega los datos.     | { "temp": 25, "city": "Madrid" }     |


**Ejemplo Práctico: Obtener el Clima**
```js
// 1. Definimos la URL de la API
const API_URL = 'https://api.openweathermap.org/data/2.5/weather?q=BuenosAires&appid=TU_API_KEY&units=metric';

// 2. Realizamos la petición
fetch(API_URL)
    .then(response => {
        // Verificamos si la respuesta es correcta (status 200)
        if (!response.ok) {
            throw new Error("Error en la petición a la API");
        }
        return response.json(); // Convertimos la respuesta a formato JSON (objeto JS)
    })
    .then(data => {
        // 3. Manipulamos los datos obtenidos
        console.log(`Ciudad: ${data.name}`);
        console.log(`Temperatura actual: ${data.main.temp}°C`);
        
        // Ejemplo de inserción en el DOM
        document.getElementById('clima-info').innerText = `En ${data.name} hacen ${data.main.temp}°C`;
    })
    .catch(error => {
        // 4. Manejo de errores
        console.error("Hubo un problema:", error);
    });
```


















































