
## Práctica Apartado 3 – Gestor de tareas

**Repositorio:** `pr_ap03_js_gestor_tareas`

---

## Objetivo

Crear una aplicación web para **gestionar una lista de tareas**, organizando toda la lógica mediante **funciones JavaScript**.

El diseño visual ya está definido mediante un archivo CSS proporcionado.
El alumno debe **construir el HTML siguiendo las indicaciones** y programar el comportamiento en JavaScript.

---

## Archivos del proyecto

El proyecto debe contener, al menos:

* `index.html`
* `styles.css` (proporcionado)
* `app.js`

---

## CSS proporcionado

Se proporciona el archivo `styles.css`.
⚠️ **No debe modificarse**.

(Se asume que el alumno lo enlaza correctamente desde el HTML.)

---

## Estructura HTML obligatoria

El archivo `index.html` debe cumplir **exactamente** con la siguiente estructura lógica.
No es necesario que coincida carácter a carácter, pero **sí en elementos e IDs**.

### 1️⃣ Estructura general

* Un elemento principal (`main`) con clase `contenedor`
* Dentro del contenedor:

  * un título principal (`h1`)
  * una sección para introducir tareas
  * una sección para mostrar la lista de tareas

---

### 2️⃣ Sección de entrada de tareas

Debe contener:

* un campo de texto para escribir la tarea

  * **id obligatorio:** `tareaInput`
* un botón para añadir la tarea

  * **id obligatorio:** `btnAgregar`
  * texto visible: `Añadir tarea`

Ambos elementos deben estar contenidos dentro de una misma sección.

---

### 3️⃣ Sección de lista de tareas

Debe contener:

* una lista (`ul`)

  * **id obligatorio:** `listaTareas`

En esta lista se añadirán dinámicamente las tareas mediante JavaScript.

---

## Enunciado funcional

Una vez creada la estructura HTML, debes implementar en `app.js` la lógica necesaria para que la aplicación funcione correctamente.

---

## Funcionalidades obligatorias

### 1️⃣ Añadir tarea

* Al pulsar el botón **“Añadir tarea”**:

  * se lee el texto del input
  * no se permiten tareas vacías
  * la tarea se añade a la lista

---

### 2️⃣ Mostrar tareas

* Cada tarea debe mostrarse como un elemento (`li`)
* El texto debe ser visible
* La página no debe recargarse

---

### 3️⃣ Marcar tarea como completada

* Cada tarea debe poder marcarse como completada
* Visualmente:

  * se debe aplicar la clase CSS `completada`
* Al volver a pulsar, debe poder desmarcarse

---

### 4️⃣ Eliminar tarea

* Cada tarea debe poder eliminarse
* Al eliminarla, debe desaparecer de la lista

---

## Organización del código (obligatoria)

La lógica debe organizarse mediante **funciones**.

Como mínimo, deben existir funciones que:

* añadan tareas
* creen el elemento visual de una tarea
* gestionen el marcado como completada
* eliminen tareas

Cada función debe tener **una única responsabilidad**.

---

## Requisitos técnicos

* JavaScript en archivo externo
* Uso de:

  * funciones declaradas o expresiones
  * funciones flecha en eventos
* Manipulación del DOM desde JavaScript
* No se permite recargar la página

---

## Entrega

* enlace al repositorio de GitHub
* enlace a la web publicada (GitHub Pages)

---

## Idea clave de la práctica

> **Un buen programa no es el que funciona,
> sino el que está bien organizado en funciones.**

