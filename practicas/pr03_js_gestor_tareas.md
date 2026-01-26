
## Práctica Apartado 3 – Gestor de tareas

**Repositorio:** `pr_ap03_js_gestor_tareas`

---

### Objetivo

Crear una aplicación web para **gestionar una lista de tareas**, organizando toda la lógica mediante **funciones JavaScript**.

El diseño visual ya está definido mediante un archivo CSS proporcionado.
El alumno debe **construir el HTML siguiendo las indicaciones** y programar el comportamiento en JavaScript.

---

### Archivos del proyecto

El proyecto debe contener, al menos:

* `index.html`
* `styles.css` (proporcionado)
* `app.js`

---

### CSS proporcionado

Se proporciona el archivo `styles.css`.
⚠️ **No debe modificarse**.

#### `styles.css`

```css
* {
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
}

body {
  background-color: #f4f6f8;
  display: flex;
  justify-content: center;
  padding-top: 40px;
}

.contenedor {
  background-color: white;
  padding: 30px;
  width: 400px;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

.entrada {
  display: flex;
  gap: 10px;
}

.entrada input {
  flex: 1;
  padding: 8px;
}

.entrada button {
  padding: 8px 12px;
  cursor: pointer;
}

.lista ul {
  margin-top: 20px;
  padding-left: 0;
}

.lista li {
  list-style: none;
  padding: 8px;
  margin-bottom: 8px;
  background-color: #eef1f4;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-radius: 4px;
}

.lista li.completada {
  text-decoration: line-through;
  color: gray;
}
```

---

### Estructura HTML obligatoria

El archivo `index.html` debe cumplir **exactamente** con la siguiente estructura lógica.
No es necesario que coincida carácter a carácter, pero **sí en elementos e IDs**.

#### 1️⃣ Estructura general

* Un elemento principal (`main`) con clase `contenedor`
* Dentro del contenedor:

  * un título principal (`h1`)
  * una sección para introducir tareas
  * una sección para mostrar la lista de tareas

---

#### 2️⃣ Sección de entrada de tareas

Debe contener:

* un campo de texto para escribir la tarea

  * **id obligatorio:** `tareaInput`
* un botón para añadir la tarea

  * **id obligatorio:** `btnAgregar`
  * texto visible: `Añadir tarea`

Ambos elementos deben estar contenidos dentro de una misma sección.

---

#### 3️⃣ Sección de lista de tareas

Debe contener:

* una lista (`ul`)

  * **id obligatorio:** `listaTareas`

En esta lista se añadirán dinámicamente las tareas mediante JavaScript.

---

### Enunciado funcional

Una vez creada la estructura HTML, debes implementar en `app.js` la lógica necesaria para que la aplicación funcione correctamente.

---

### Funcionalidades obligatorias

#### 1️⃣ Añadir tarea

* Al pulsar el botón **“Añadir tarea”**:

  * se lee el texto del input
  * no se permiten tareas vacías
  * la tarea se añade a la lista

---

#### 2️⃣ Mostrar tareas

* Cada tarea debe mostrarse como un elemento (`li`)
* El texto debe ser visible
* La página no debe recargarse

---

#### 3️⃣ Marcar tarea como completada

* Cada tarea debe poder marcarse como completada
* Visualmente:

  * se debe aplicar la clase CSS `completada`
* Al volver a pulsar, debe poder desmarcarse

---

#### 4️⃣ Eliminar tarea

* Cada tarea debe poder eliminarse
* Al eliminarla, debe desaparecer de la lista

---

### Organización del código (obligatoria)

La lógica debe organizarse mediante **funciones**.

Como mínimo, deben existir funciones que:

* añadan tareas
* creen el elemento visual de una tarea
* gestionen el marcado como completada
* eliminen tareas

Cada función debe tener **una única responsabilidad**.

---

### Requisitos técnicos

* JavaScript en archivo externo
* Uso de:

  * funciones declaradas y funciones `Expression`
  * funciones flecha en eventos

* Manipulación del DOM desde JavaScript
* No se permite recargar la página

---

### Entrega

* enlace al repositorio de GitHub
* enlace a la web publicada (GitHub Pages)

---

### Idea clave de la práctica

> **Un buen programa no es el que funciona,
> sino el que está bien organizado en funciones.**

---

Sí, te has explicado **perfectamente**, y la idea es **muy buena didácticamente** 👍
Aquí tienes **solo el subapartado “Ayuda”**, redactado **para el alumnado**, con explicaciones claras, ejemplos **genéricos** (no relacionados directamente con la práctica) y cubriendo los métodos que **necesitan conocer** para poder resolverla por sí mismos.

Lo puedes insertar **tal cual** justo antes de “Entrega”.

---

### Ayuda: Métodos del DOM útiles para esta práctica

Para poder crear y modificar elementos en una página web usando JavaScript, es necesario conocer algunos **métodos básicos del DOM**.
Estos métodos se usan constantemente en aplicaciones web reales y te permitirán **crear elementos**, **añadirlos a la página**, **modificar su aspecto** y **eliminarlos**.

---

#### 1️⃣ `document.createElement()`

Permite **crear un nuevo elemento HTML desde JavaScript**.

Sintaxis:

```js
const elemento = document.createElement("etiqueta");
```

Ejemplo:

```js
const parrafo = document.createElement("p");
parrafo.textContent = "Hola desde JavaScript";
```

👉 Este código **crea** un `<p>`, pero **aún no aparece en la página**.
Para que se vea, hay que añadirlo al DOM (ver `appendChild`).

---

#### 2️⃣ `appendChild()`

Añade un elemento **como hijo** de otro elemento del DOM.

Sintaxis:

```js
padre.appendChild(hijo);
```

Ejemplo:

```js
const contenedor = document.querySelector("#contenedor");
const mensaje = document.createElement("p");

mensaje.textContent = "Mensaje añadido dinámicamente";
contenedor.appendChild(mensaje);
```

Resultado en el HTML:

```html
<div id="contenedor">
  <p>Mensaje añadido dinámicamente</p>
</div>
```

👉 Es uno de los métodos **más importantes** para crear contenido dinámico.

---

#### 3️⃣ `classList`

Permite **gestionar clases CSS** desde JavaScript.

**➕ `classList.add()`**

Añade una clase:

```js
elemento.classList.add("activo");
```

**➖ `classList.remove()`**

Elimina una clase:

```js
elemento.classList.remove("activo");
```

**🔁 `classList.toggle()`**

Añade la clase si no existe y la quita si ya existe.

```js
elemento.classList.toggle("activo");
```

Ejemplo completo:

```js
const caja = document.querySelector(".caja");

caja.addEventListener("click", () => {
  caja.classList.toggle("resaltado");
});
```

👉 `toggle` es muy útil para **activar / desactivar estados visuales**.

---

#### 4️⃣ `remove()`

Elimina un elemento **directamente del DOM**.

Ejemplo:

```js
const aviso = document.querySelector(".aviso");
aviso.remove();
```

👉 El elemento desaparece completamente de la página.

Este método se usa habitualmente para:

* borrar elementos creados dinámicamente
* eliminar mensajes
* eliminar ítems de una lista

---

#### 5️⃣ `textContent` vs `innerHTML`

**`textContent`**

Inserta **solo texto**, sin interpretar HTML.

```js
elemento.textContent = "Texto plano";
```

**`innerHTML`**

Inserta texto **interpretando etiquetas HTML**.

```js
elemento.innerHTML = "<strong>Texto en negrita</strong>";
```

👉 Recomendación general:

* usa `textContent` siempre que sea posible
* usa `innerHTML` solo cuando necesites etiquetas HTML

---

#### 6️⃣ `addEventListener()`

Permite **asociar una función a un evento**.

Sintaxis:

```js
elemento.addEventListener("evento", funcion);
```

Ejemplo:

```js
const boton = document.querySelector("#btn");

boton.addEventListener("click", () => {
  console.log("Botón pulsado");
});
```

👉 Es la forma moderna y recomendada de trabajar con eventos.

---

#### 7️⃣ `parentElement`

Permite acceder al **elemento padre** de otro elemento.

Ejemplo:

```js
const boton = document.querySelector("button");
const contenedor = boton.parentElement;
```

👉 Muy útil cuando un evento ocurre en un botón y se quiere actuar sobre su contenedor.

---

#### 8️⃣ Resumen de métodos útiles

| Método / Propiedad   | Para qué sirve                 |
| -------------------- | ------------------------------ |
| `createElement()`    | Crear elementos HTML           |
| `appendChild()`      | Añadir elementos al DOM        |
| `classList.add()`    | Añadir una clase CSS           |
| `classList.remove()` | Eliminar una clase CSS         |
| `classList.toggle()` | Activar / desactivar una clase |
| `remove()`           | Eliminar un elemento del DOM   |
| `textContent`        | Insertar texto plano           |
| `innerHTML`          | Insertar HTML                  |
| `addEventListener()` | Escuchar eventos               |
| `parentElement`      | Acceder al elemento padre      |

---

#### Idea clave

> **JavaScript no solo modifica datos:
> crea, modifica y elimina elementos HTML en tiempo real.**

Con estos métodos ya tienes las herramientas necesarias para construir interfaces dinámicas y resolver esta práctica organizando la lógica mediante funciones.

---
