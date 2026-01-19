
# JavaScript – Introducción y primeros conceptos

---

## 1. ¿Qué es JavaScript?

JavaScript es un **lenguaje de programación** que se utiliza para añadir **lógica, interactividad y comportamiento dinámico** a las páginas web.

Con HTML y CSS podemos crear páginas:

* estructuradas
* visualmente atractivas

Pero con un comportamiento **muy limitado**.

JavaScript permite que una página:

* tome decisiones
* repita acciones
* trabaje con datos del usuario
* reaccione a eventos
* modifique su contenido en tiempo real

👉 JavaScript es el lenguaje que permite **programar la web**, no solo diseñarla.

---

## 2. ¿Puede HTML5 y CSS3 introducir comportamiento?

HTML5 y CSS3 pueden introducir **cierto comportamiento**, pero de forma **limitada y automática**.

Ejemplos:

* campos obligatorios en formularios
* botones deshabilitados
* cambios visuales con `:hover`
* animaciones CSS
* elementos desplegables (`<details>`)

Este comportamiento:

* no depende de lógica compleja
* no toma decisiones
* no se adapta a distintos valores

👉 Cuando necesitamos **condiciones**, **repeticiones** o **trabajar con datos**, necesitamos JavaScript.

---

## 3. ¿Dónde se ejecuta JavaScript?

En esta unidad, JavaScript se ejecuta **en el navegador web**.

El navegador:

1. carga el HTML
2. interpreta el CSS
3. ejecuta el JavaScript

Esto implica que:

* no hay compilación previa
* los errores aparecen en tiempo real
* el código se ejecuta directamente

---

## 4. El navegador como entorno de trabajo

El navegador incluye herramientas para:

* ejecutar JavaScript
* ver errores
* analizar el comportamiento del código
* probar instrucciones

Estas herramientas se llaman **Herramientas de desarrollador**.

---

### 4.1 La consola

La consola permite que el programa muestre mensajes **para el programador**.

```js
console.log("Mensaje de prueba");
```

Estos mensajes:

* no los ve el usuario
* sirven para comprobar valores
* ayudan a depurar errores

---

### 4.2 Errores en la consola

Cuando JavaScript encuentra un error:

* se muestra un mensaje en rojo
* se indica el archivo y la línea

Ejemplo:

```js
console.loge("Hola");
```

Aprender a **leer errores** es parte fundamental de programar.

---

### 4.3 La consola como intérprete interactivo

La consola permite escribir JavaScript directamente:

```js
5 * 4
```

Resultado inmediato:

```
20
```

Esto permite:

* probar ideas
* entender cómo funciona una instrucción
* experimentar sin crear archivos

---

### 4.4 Mostrar mensajes al usuario: `alert`

JavaScript puede mostrar mensajes visibles para el usuario mediante ventanas emergentes.

```js
alert("Mensaje informativo");
```

Este tipo de mensaje:

* aparece en un pop-up
* bloquea la página hasta aceptarlo
* se usa para avisos y pruebas sencillas

---

## 5. ¿Qué es el DOM?

Cuando el navegador carga una página:

* convierte el HTML en una estructura interna
* cada etiqueta se convierte en un objeto
* se organiza en forma de árbol

A esta estructura se le llama **DOM (Document Object Model)**.

Gracias al DOM, JavaScript puede:

* acceder a elementos de la página
* leer su contenido
* modificar textos
* cambiar estilos
* crear o eliminar elementos

👉 El DOM es el **puente entre JavaScript y la página web**.

---

## 6. Cómo se usa JavaScript en una web

JavaScript puede escribirse:

* dentro del HTML
* en archivos externos

La forma recomendada es usar **archivos `.js` externos**.

```html
<script src="app.js" defer></script>
```

Esto permite:

* separar contenido y lógica
* mantener el código ordenado
* evitar errores de carga

---

### ¿Qué significa `defer`?

* el navegador carga primero el HTML
* después ejecuta el JavaScript
* asegura que la página ya existe cuando se ejecuta el código

---

## 7. Estructura básica de una web con JavaScript

Una web con JavaScript suele tener:

* un archivo HTML
* uno o varios archivos `.js`

Ejemplo mínimo en JavaScript:

```js
console.log("El script se ha cargado correctamente");
```

Si el mensaje aparece en la consola, el script está funcionando.

---

## 8. Variables y constantes

Un programa necesita **guardar información**.
Para ello se usan **variables**.

---

### 8.1 Constantes (`const`)

Se usan cuando el valor **no debe cambiar**.

```js
const IVA = 21;
```

---

### 8.2 Variables (`let`)

Se usan cuando el valor **puede cambiar**.

```js
let contador = 0;
contador = contador + 1;
```

---

👉 Regla recomendada:

* usar `const` por defecto
* usar `let` solo si el valor cambia

---

## 9. Tipos de datos básicos

### Texto (string)

```js
const ciudad = "Madrid";
```

---

### Número

```js
const temperatura = 25;
```

---

### Booleano

```js
const activo = true;
```

---

### Plantillas literales

Permiten crear textos combinando variables:

```js
const producto = "Libro";
console.log(`Producto seleccionado: ${producto}`);
```

---

## 10. Estructuras de control (decisiones)

Permiten ejecutar código **según una condición**.

---

### `if`

```js
if (valor > 10) {
  console.log("Valor alto");
}
```

---

### `if / else`

```js
if (valor > 10) {
  console.log("Alto");
} else {
  console.log("Normal o bajo");
}
```

---

### `else if`

```js
if (valor > 20) {
  console.log("Muy alto");
} else if (valor > 10) {
  console.log("Alto");
} else {
  console.log("Normal");
}
```

---

### Operador condicional (ternario)

```js
const estado = valor > 10 ? "Alto" : "Normal";
```

---

## 11. Estructuras de repetición (bucles)

Permiten **repetir una acción varias veces**.

---

### `for`

```js
for (let i = 0; i < 5; i++) {
  console.log("Iteración");
}
```

---

### `while`

```js
let x = 0;

while (x < 3) {
  console.log(x);
  x++;
}
```

---

### `do...while`

```js
let x = 0;

do {
  console.log(x);
  x++;
} while (x < 3);
```

---

### `break` y `continue`

```js
for (let i = 1; i <= 5; i++) {
  if (i === 3) continue;
  console.log(i);
}
```

---

## 12. Acceder a elementos del DOM (leer datos)

Para trabajar con la página, JavaScript primero debe **localizar un elemento del DOM**.
Existen varias formas de hacerlo. Aquí verás las más importantes.

---

### 12.1 Selección clásica: `getElementById`

```js
document.getElementById("identificador");
```

* Busca un elemento por su `id`
* Devuelve el elemento (o `null` si no existe)

Ejemplo genérico:

```js
const elemento = document.getElementById("titulo");
```

---

### 12.2 Selección moderna: `querySelector`

`querySelector` es una forma **moderna y muy flexible** de seleccionar elementos, porque utiliza **selectores CSS**.

```js
document.querySelector("selectorCSS");
```

* Devuelve **el primer elemento** que coincide con el selector
* Si no encuentra nada, devuelve `null`
* Permite seleccionar por:

  * `#id`
  * `.clase`
  * `etiqueta`
  * selectores combinados

Ejemplos genéricos:

```js
const porId = document.querySelector("#titulo");
const porClase = document.querySelector(".destacado");
const porEtiqueta = document.querySelector("h2");
const combinado = document.querySelector("section .destacado");
```

👉 Si hay varios elementos que coinciden, `querySelector` devuelve **solo el primero**.

---

### 12.3 Seleccionar varios: `querySelectorAll`

Si necesitas **todos** los elementos que coinciden con un selector, usas:

```js
document.querySelectorAll("selectorCSS");
```

* Devuelve una lista de elementos (un **NodeList**)
* Puede estar vacía si no hay coincidencias
* Normalmente se recorre con `for...of` o `forEach`

Ejemplo genérico:

```js
const items = document.querySelectorAll(".item");

for (const item of items) {
  console.log(item.textContent);
}
```

---

### 12.4 ¿Cuándo usar cada uno?

* `getElementById("id")`
  ✔ simple, directo, muy común en ejemplos básicos
  ✔ ideal cuando sabes que hay un único elemento por id

* `querySelector("#id")`
  ✔ moderno y flexible
  ✔ permite usar selectores CSS (igual que en CSS)

* `querySelectorAll(".clase")`
  ✔ cuando necesitas varios elementos

👉 En proyectos modernos es muy habitual usar `querySelector` / `querySelectorAll` como forma principal.

---

### 12.5 Obtener el valor de un elemento de formulario

Los elementos de formulario usan la propiedad **`.value`**.

```js
const campo = document.querySelector("#campo");
const contenido = campo.value;
```

👉 `.value` devuelve **texto**, aunque el usuario escriba números.

---

### 12.6 Conversión a número

```js
const numero = Number(campo.value);
```

---

## 13. Escribir información en el DOM (mostrar resultados)

JavaScript no muestra resultados automáticamente:
hay que **escribirlos en la página**.

---

### `textContent`

```js
elemento.textContent = "Texto simple";
```

* escribe texto
* no interpreta HTML

---

### `innerHTML`

```js
elemento.innerHTML = "<strong>Texto</strong>";
```

* interpreta HTML
* permite etiquetas y formato

⚠️ Importante: `innerHTML` es potente, pero hay que usarlo con cuidado si el contenido proviene del usuario.

---

## 14. Eventos: asociar acciones a la página

JavaScript se ejecuta **cuando ocurre algo**.
Ese “algo” se llama **evento**.

Ejemplos:

* clic
* envío de formulario
* pulsación de tecla

---

### `addEventListener`

```js
elemento.addEventListener("click", function () {
  console.log("Evento detectado");
});
```

Esto significa:

> “Cuando ocurra este evento, ejecuta este código”.

---

### ¿Qué es la función que se pasa al evento?

La función que escribimos dentro de `addEventListener` es el código que se ejecutará **más tarde**, cuando ocurra el evento.

A esto se le llama **callback** (función que se llama “de vuelta” cuando pasa algo).

---

### El evento `submit` y `preventDefault`

Los formularios, por defecto:

* envían los datos
* recargan la página

Para evitarlo:

```js
evento.preventDefault();
```

Esto permite que JavaScript controle el proceso.

---

<a id="practica1"></a>
## 15. Práctica 1 – Saludos festivos 🎉 <a

En esta práctica vas a **combinar e investigar** los conceptos vistos.

No es necesario terminarla en clase, pero si debéis entregarla y traerla el próximo día que tengamos clase del módulo de LM.

---

### 📌 Enunciado

Crea una página web con:

* Un formulario que pregunte:

  * cómo te llamas
  * qué edad tienes
* Un botón con el texto **“Saludar”**

Al pulsar el botón debe mostrarse un mensaje con:

```
Hola <nombre>!
```

Además:

* Si la persona es **menor de edad**:

  * mostrar el texto **“Brindemos con”**
  * mostrar tantos 🥛 como años tenga

* Si la persona es **mayor de edad**:

  * mostrar el mismo texto
  * mostrar tantas 🍺 como años tenga

---

### 📌 Indicaciones

Para resolver esta práctica necesitarás:

* acceder a elementos del DOM (por `id` o con selectores)
* obtener valores de un formulario (`value`)
* usar variables y constantes
* tomar decisiones con `if / else` (o ternario si quieres)
* repetir acciones con bucles
* escribir resultados en la página (`textContent` o `innerHTML`)
* asociar código a un evento

No es necesario que esté perfecta.
Lo importante es **pensar, investigar y entender**.
