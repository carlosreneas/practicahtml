# Actividad práctica: HTML, CSS y JavaScript paso a paso

## Proyecto: Dashboard de Usuarios

### Objetivo general

Construir de forma incremental una aplicación web tipo **Dashboard**, comenzando con HTML básico, agregando estilos con CSS y finalizando con JavaScript para consumir datos desde una API externa usando `fetch()`.

La intención de la actividad es comprender claramente el papel de cada tecnología:

- **HTML**: define la estructura y el contenido.
- **CSS**: define la presentación y apariencia.
- **JavaScript**: agrega comportamiento e interacción.
- **Fetch / API REST**: permite obtener información externa.

---

# 1. Estructura inicial del proyecto

Crear una carpeta llamada:

```text
dashboard/
```

Dentro de ella crear la siguiente estructura:

```text
dashboard/
│
├── index.html
├── css/
│   └── style.css
└── js/
    └── app.js
```

---

# 2. Primera página HTML

Crear el archivo `index.html`:

```html
<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Mi Dashboard</title>
</head>

<body>

    <h1>Dashboard de Usuarios</h1>

    <p>Bienvenido a nuestra aplicación web.</p>

</body>

</html>
```

## Conceptos para explicar

En esta primera etapa se pueden introducir:

- `<!DOCTYPE html>`
- `<html>`
- `<head>`
- `<body>`
- etiquetas HTML
- elementos HTML
- atributos
- etiquetas de apertura y cierre
- anidamiento
- estructura jerárquica
- introducción al DOM

Ejemplo:

```html
<h1>Dashboard de Usuarios</h1>
```

Este elemento contiene:

```text
Etiqueta inicial
    ↓
   <h1>

Contenido
    ↓
Dashboard de Usuarios

Etiqueta final
    ↓
   </h1>
```

---

# 3. Crear la estructura del Dashboard

Ahora se agregará HTML semántico.

```html
<body>

    <header>
        <h1>Mi Dashboard</h1>
    </header>

    <nav>
        <ul>
            <li><a href="#">Inicio</a></li>
            <li><a href="#">Usuarios</a></li>
            <li><a href="#">Reportes</a></li>
            <li><a href="#">Configuración</a></li>
        </ul>
    </nav>

    <main>

        <section>

            <h2>Resumen</h2>

            <article>
                <h3>Usuarios</h3>
                <p>150</p>
            </article>

            <article>
                <h3>Usuarios activos</h3>
                <p>42</p>
            </article>

            <article>
                <h3>Nuevos usuarios</h3>
                <p>18</p>
            </article>

        </section>

    </main>

    <footer>
        <p>Universidad Simón Bolívar - 2026</p>
    </footer>

</body>
```

## Conceptos para explicar

- HTML semántico.
- `<header>`
- `<nav>`
- `<main>`
- `<section>`
- `<article>`
- `<footer>`

Pregunta para los estudiantes:

> ¿Por qué es mejor utilizar etiquetas semánticas en lugar de construir toda la página usando únicamente `<div>`?

---

# 4. Agregar una tabla de usuarios

Dentro de `<main>` agregar:

```html
<section>

    <h2>Usuarios registrados</h2>

    <table>

        <thead>

            <tr>
                <th>Nombre</th>
                <th>Email</th>
                <th>Ciudad</th>
            </tr>

        </thead>

        <tbody>

            <tr>
                <td>Carlos</td>
                <td>carlos@email.com</td>
                <td>Cúcuta</td>
            </tr>

        </tbody>

    </table>

</section>
```

## Conceptos para explicar

- `<table>`
- `<thead>`
- `<tbody>`
- `<tr>`
- `<th>`
- `<td>`

Hasta este momento toda la página funciona únicamente con HTML.

---

# 5. Introducción a CSS

Dentro del `<head>` conectar el archivo CSS:

```html
<link rel="stylesheet" href="css/style.css">
```

Crear `css/style.css`:

```css
body {
    font-family: Arial, sans-serif;
}

header {
    background: #222;
    color: white;
    padding: 20px;
}
```

## Anatomía de una regla CSS

```css
header {
    background: #222;
}
```

Interpretación:

```text
header      → selector
background  → propiedad
#222        → valor
```

---

# 6. Estilizar el menú de navegación

Agregar:

```css
nav ul {
    list-style: none;
}

nav a {
    text-decoration: none;
}
```

## Conceptos para explicar

- selector de etiqueta
- selector de clase
- selector por ID
- selector descendente
- propiedades CSS
- valores CSS

---

# 7. Crear tarjetas de indicadores

Modificar los indicadores:

```html
<div class="cards">

    <article class="card">

        <h3>Usuarios</h3>

        <p id="totalUsuarios">
            150
        </p>

    </article>

    <article class="card">

        <h3>Activos</h3>

        <p>42</p>

    </article>

    <article class="card">

        <h3>Nuevos</h3>

        <p>18</p>

    </article>

</div>
```

CSS:

```css
.cards {
    display: flex;
    gap: 20px;
}

.card {
    border: 1px solid #ddd;
    padding: 20px;
    border-radius: 8px;
}
```

## Conceptos para explicar

- clases CSS
- reutilización de estilos
- modelo de cajas
- `padding`
- `border`
- `border-radius`
- `display: flex`
- `gap`

Estructura:

```text
.cards
│
├── .card
├── .card
└── .card
```

---

# 8. Crear el layout del Dashboard

Modificar la estructura:

```html
<div class="layout">

    <aside class="sidebar">

        <h2>Dashboard</h2>

        <nav>

            <ul>

                <li>
                    <a href="#">
                        Inicio
                    </a>
                </li>

                <li>
                    <a href="#">
                        Usuarios
                    </a>
                </li>

                <li>
                    <a href="#">
                        Reportes
                    </a>
                </li>

            </ul>

        </nav>

    </aside>

    <main class="content">

        <!-- Contenido principal -->

    </main>

</div>
```

CSS:

```css
.layout {
    display: flex;
    min-height: 100vh;
}

.sidebar {
    width: 220px;
    background: #222;
    color: white;
    padding: 20px;
}

.content {
    flex: 1;
    padding: 30px;
}
```

---

# 9. Diseño Responsive

Reducir el tamaño del navegador.

Observar qué ocurre con la interfaz.

Luego agregar:

```css
@media (max-width: 768px) {

    .layout {
        flex-direction: column;
    }

    .sidebar {
        width: 100%;
    }

    .cards {
        flex-direction: column;
    }

}
```

## Conceptos para explicar

- Responsive Web Design.
- Media Queries.
- Breakpoints.
- Diseño adaptable.
- Mobile First.

También explicar la importancia de:

```html
<meta
    name="viewport"
    content="width=device-width, initial-scale=1.0">
```

---

# 10. Introducción a JavaScript

Conectar JavaScript antes del cierre de `body`:

```html
<script src="js/app.js"></script>
```

Crear:

```text
js/app.js
```

Primera prueba:

```javascript
console.log("JavaScript funcionando");
```

Abrir las herramientas del navegador:

```text
F12
→ Console
```

---

# 11. Introducción al DOM

Agregar:

```javascript
const titulo =
    document.querySelector("h1");

console.log(titulo);
```

Explicar la relación:

```text
HTML
 ↓
DOM
 ↓
JavaScript
```

El navegador interpreta el HTML y crea una representación denominada **DOM - Document Object Model**.

JavaScript puede consultar y modificar ese DOM.

---

# 12. Modificar elementos con JavaScript

HTML:

```html
<p id="totalUsuarios">
    150
</p>
```

JavaScript:

```javascript
const total =
    document.querySelector(
        "#totalUsuarios"
    );

total.textContent = "200";
```

Esto permite explicar la diferencia:

```text
HTML       → estructura
CSS        → presentación
JavaScript → comportamiento
```

---

# 13. Agregar interacción con un botón

HTML:

```html
<button id="btnCargar">
    Cargar usuarios
</button>
```

JavaScript:

```javascript
const boton =
    document.querySelector(
        "#btnCargar"
    );

boton.addEventListener(
    "click",
    function () {

        console.log(
            "El usuario hizo clic"
        );

    }
);
```

## Conceptos para explicar

- eventos
- `click`
- `addEventListener`
- funciones
- interacción del usuario

---

# 14. Introducción a las APIs

Hasta ahora los datos se encuentran escritos directamente en el HTML.

Una aplicación real normalmente obtiene información desde un servidor.

Arquitectura simplificada:

```text
Navegador
   │
   │ HTTP
   ▼
API REST
   │
   ▼
JSON
```

Para esta actividad utilizaremos la API pública:

```text
https://jsonplaceholder.typicode.com/users
```

---

# 15. Primera petición con Fetch

JavaScript:

```javascript
fetch(
    "https://jsonplaceholder.typicode.com/users"
)
.then(response => response.json())
.then(data => {

    console.log(data);

});
```

Abrir:

```text
F12
→ Console
```

Analizar los datos recibidos.

---

# 16. Fetch usando async / await

Crear la función:

```javascript
async function obtenerUsuarios() {

    const respuesta =
        await fetch(
            "https://jsonplaceholder.typicode.com/users"
        );

    const usuarios =
        await respuesta.json();

    console.log(
        usuarios
    );

}

obtenerUsuarios();
```

## Conceptos para explicar

- asincronía
- `async`
- `await`
- `Promise`
- HTTP
- JSON

---

# 17. Mostrar los usuarios en la tabla

Modificar el HTML:

```html
<tbody id="tablaUsuarios">

</tbody>
```

JavaScript:

```javascript
async function obtenerUsuarios() {

    const respuesta =
        await fetch(
            "https://jsonplaceholder.typicode.com/users"
        );

    const usuarios =
        await respuesta.json();

    mostrarUsuarios(
        usuarios
    );

}
```

Crear:

```javascript
function mostrarUsuarios(
    usuarios
) {

    const tabla =
        document.querySelector(
            "#tablaUsuarios"
        );

    tabla.innerHTML = "";

    usuarios.forEach(
        usuario => {

            tabla.innerHTML += `
                <tr>
                    <td>
                        ${usuario.name}
                    </td>

                    <td>
                        ${usuario.email}
                    </td>

                    <td>
                        ${usuario.address.city}
                    </td>
                </tr>
            `;

        }
    );

}
```

## Conceptos para explicar

- arreglos
- objetos
- `forEach`
- propiedades
- template strings
- interpolación
- modificación del DOM

Ejemplos:

```javascript
usuario.name
```

```javascript
usuario.email
```

```javascript
usuario.address.city
```

---

# 18. Actualizar indicadores del Dashboard

Después de obtener los usuarios:

```javascript
document
    .querySelector(
        "#totalUsuarios"
    )
    .textContent =
        usuarios.length;
```

La función podría quedar:

```javascript
async function obtenerUsuarios() {

    const respuesta =
        await fetch(
            "https://jsonplaceholder.typicode.com/users"
        );

    const usuarios =
        await respuesta.json();

    mostrarUsuarios(
        usuarios
    );

    document
        .querySelector(
            "#totalUsuarios"
        )
        .textContent =
            usuarios.length;

}
```

Ahora el Dashboard utiliza datos reales provenientes del servicio.

---

# 19. Manejo de errores

Modificar la función:

```javascript
async function obtenerUsuarios() {

    try {

        const respuesta =
            await fetch(
                "https://jsonplaceholder.typicode.com/users"
            );

        if (!respuesta.ok) {

            throw new Error(
                "Error al consultar usuarios"
            );

        }

        const usuarios =
            await respuesta.json();

        mostrarUsuarios(
            usuarios
        );

    }
    catch (error) {

        console.error(
            error
        );

    }

}
```

## Conceptos para explicar

- errores
- excepciones
- `try`
- `catch`
- validación de respuestas HTTP

---

# 20. Estado de carga

Agregar:

```html
<p id="mensaje">
    Presione cargar usuarios
</p>
```

JavaScript:

```javascript
const mensaje =
    document.querySelector(
        "#mensaje"
    );

mensaje.textContent =
    "Cargando...";
```

Cuando termine:

```javascript
mensaje.textContent =
    "Usuarios cargados";
```

Si ocurre un error:

```javascript
mensaje.textContent =
    "No fue posible cargar los usuarios";
```

Esto permite introducir el concepto de **estado de la interfaz**.

---

# 21. Resultado conceptual

Durante la actividad los estudiantes deberían comprender:

```text
HTML
¿Qué existe en la página?

CSS
¿Cómo se ve?

JavaScript
¿Qué hace?

Fetch / API
¿De dónde vienen los datos?
```

---

# 22. Flujo completo de aprendizaje

| Etapa | Tema | Concepto |
|---|---|---|
| 1 | Página inicial | HTML |
| 2 | Estructura semántica | HTML semántico |
| 3 | Tabla | Elementos HTML |
| 4 | Estilos | CSS |
| 5 | Tarjetas | Clases |
| 6 | Dashboard | Flexbox |
| 7 | Responsive | Media Queries |
| 8 | JavaScript inicial | JS |
| 9 | Manipulación | DOM |
| 10 | Botón | Eventos |
| 11 | API | Fetch |
| 12 | Asincronía | async / await |
| 13 | Mostrar datos | DOM + Arrays |
| 14 | Indicadores | Datos dinámicos |
| 15 | Errores | try / catch |
| 16 | Estados | UX |

---

# 23. Retos para los estudiantes

## Reto 1

Agregar una cuarta tarjeta:

```text
Ciudades
```

Mostrar cuántas ciudades diferentes existen entre los usuarios.

---

## Reto 2

Agregar un campo:

```html
<input
    type="text"
    id="buscar"
    placeholder="Buscar usuario">
```

Filtrar usuarios por nombre.

---

## Reto 3

Agregar un botón:

```text
Actualizar
```

Que vuelva a consultar la API.

---

## Reto 4

Modificar el diseño para que en dispositivos móviles:

- el menú quede arriba
- las tarjetas estén una debajo de otra
- la tabla se adapte al ancho disponible

---

## Reto 5

Agregar un botón por usuario:

```text
Ver detalle
```

Cuando el usuario haga clic debe mostrarse:

- nombre
- email
- teléfono
- ciudad
- empresa

---

# 24. Preguntas de cierre

1. ¿Cuál es la función principal de HTML?
2. ¿Cuál es la función principal de CSS?
3. ¿Cuál es la función principal de JavaScript?
4. ¿Qué es el DOM?
5. ¿Qué es una API?
6. ¿Qué hace `fetch()`?
7. ¿Qué significa trabajar de forma asíncrona?
8. ¿Cuál es la diferencia entre datos estáticos y datos dinámicos?
9. ¿Qué ocurre si una API no responde?
10. ¿Por qué una interfaz debe ser responsive?

---

# 25. Conclusión

Al finalizar la actividad, el estudiante habrá construido una pequeña aplicación web completa siguiendo una evolución natural:

```text
Página estática
      ↓
HTML semántico
      ↓
Diseño CSS
      ↓
Dashboard
      ↓
Responsive
      ↓
JavaScript
      ↓
DOM
      ↓
Eventos
      ↓
Fetch
      ↓
API REST
      ↓
Datos dinámicos
```

La idea central es que cada tecnología aparezca para resolver una necesidad concreta:

> **HTML define qué existe. CSS define cómo se ve. JavaScript define qué hace. Una API proporciona los datos.**
