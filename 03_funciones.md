
## 3. Funciones en JavaScript

Las **funciones** son el mecanismo principal para **organizar un programa**: permiten agrupar instrucciones, darles un nombre, reutilizarlas y combinarlas para construir aplicaciones más grandes.

En programación web, además, las funciones se usan constantemente para **responder a eventos** (clics, formularios, teclas, foco…), por lo que dominarlas es imprescindible. ([developer.mozilla.org][2])

---

### 3.1. Qué es una función

Una **función** es un bloque de código que se ejecuta **solo cuando se invoca** (cuando se llama).

* Puede **recibir datos** (parámetros).
* Puede **devolver un resultado** (`return`).
* Puede **no devolver nada**, y entonces su resultado será `undefined`. ([javascript.info][1])

Ejemplo mínimo:

```js
function saludar() {
  console.log("Hola");
}

saludar(); // ejecuta el código de la función
```

---

### 3.2. Declaración de funciones

La forma más clásica es la **declaración de función**:

```js
function mostrarMensaje() {
  console.log("Mensaje desde una función");
}
```

Elementos de la declaración:

* `function` (palabra reservada)
* nombre de la función (convención: verbos o “acciones”)
* paréntesis `()` con parámetros (o vacío)
* cuerpo `{ ... }`

Las declaraciones de función tienen una característica importante: **pueden “aparecer” después de la llamada y aun así funcionar**, debido al hoisting (lo verás en el apartado 3.7). ([developer.mozilla.org][3])

---

### 3.3. Parámetros y argumentos

* **Parámetros**: nombres que “recibe” la función al definirse.
* **Argumentos**: valores reales que se pasan al llamar.

```js
function saludar(nombre) {       // parámetro: nombre
  console.log("Hola " + nombre);
}

saludar("Miguel");               // argumento: "Miguel"
saludar("Carmen");
```

#### 3.3.1. Parámetros por defecto

Si un argumento no se pasa, el parámetro queda como `undefined`. A veces interesa definir un valor por defecto:

```js
function saludar(nombre = "invitado") {
  console.log("Hola " + nombre);
}

saludar();         // Hola invitado
saludar("Diego");  // Hola Diego
```

Esto es muy habitual en código real cuando un dato puede faltar.

---

### 3.4. `return`: devolver valores y cortar la ejecución

Una función puede devolver un resultado con `return`. El `return`:

1. devuelve el valor
2. **termina la función inmediatamente** (no se ejecuta lo que haya después)

```js
function sumar(a, b) {
  return a + b;
}

const r = sumar(2, 3);
console.log(r); // 5
```

Ejemplo de “salida temprana” (muy común en validaciones):

```js
function esMayorDeEdad(edad) {
  if (edad < 0) return false;  // salida temprana
  return edad >= 18;
}
```

Si una función no hace `return`, su resultado es `undefined`:

```js
function imprimir() {
  console.log("Hola");
}

const x = imprimir();
console.log(x); // undefined
```

---

### 3.5. Funciones útiles en la práctica: ejemplo con `Math`

JavaScript incluye objetos con utilidades incorporadas. `Math` es uno de los más usados.

* `Math.random()` devuelve un número aleatorio `0 <= n < 1`
* `Math.floor(x)` redondea hacia abajo

Ejemplo completo: número aleatorio entre 1 y 10

```js
function getRandomNumber1a10() {
  const random = Math.random();        // 0 <= n < 1
  const multiplied = random * 10;      // 0 <= n < 10
  const rounded = Math.floor(multiplied); // 0..9
  return rounded + 1;                  // 1..10
}
```

En código real, lo habitual es simplificar:

```js
function getRandomNumber1a10() {
  return Math.floor(Math.random() * 10) + 1;
}
```

---

### 3.6. El orden de los parámetros importa

Una función espera los argumentos en el mismo orden que los parámetros.

```js
function cocinarMicroondas(plato, tiempo, potencia) {
  if (plato === "🥚" && tiempo === 2 && potencia === 3) return "🍳";
  return "❌ Plato no soportado";
}

console.log(cocinarMicroondas("🥚", 2, 3)); // 🍳
console.log(cocinarMicroondas(2, 3, "🥚")); // ❌ Plato no soportado
```

Este tipo de errores es muy frecuente al empezar: **mismo dato, orden incorrecto**.

---

### 3.7. Function Expression (funciones como valor)

En JavaScript, una función es **un valor**, así que puede guardarse en variables. Esto se llama **function expression**. ([javascript.info][4])

```js
const sumar = function (a, b) {
  return a + b;
};

console.log(sumar(4, 5)); // 9
```

Aquí la función no tiene nombre (“anónima”) y se asigna a `sumar`.

#### 3.7.1. Cuándo se usan function expressions

Se usan muchísimo cuando:

* una función se pasa como parámetro (callbacks)
* una función se crea “en el momento”
* una función depende de una condición

Ejemplo: elegir comportamiento en tiempo de ejecución:

```js
let operacion;

const modo = "suma";

if (modo === "suma") {
  operacion = function (a, b) {
    return a + b;
  };
} else {
  operacion = function (a, b) {
    return a - b;
  };
}

console.log(operacion(10, 3)); // 13
```

---

### 3.8. Hoisting en funciones

**Hoisting** es el comportamiento por el cual ciertas declaraciones “están disponibles” antes en el flujo del programa.

#### 3.8.1. Hoisting en "Function Declaration"

Esto funciona:

```js
console.log(sumar(2, 3)); // 5

function sumar(a, b) {
  return a + b;
}
```

Porque las declaraciones de función pueden ser “elevadas” (hoisted). ([developer.mozilla.org][3])

#### 3.8.2. No hay hoisting en "Function Expression"

Esto NO funciona:

```js
console.log(sumar(2, 3)); // ReferenceError

const sumar = function (a, b) {
  return a + b;
};
```

La variable `sumar` (con `const`) existe, pero no se puede usar antes de inicializarse con la función.

---

### 3.9. Arrow Functions (Funciones flecha)

Las funciones flecha son una forma más concisa de escribir function expressions:

```js
const sumar = (a, b) => {
  return a + b;
};
```

#### 3.9.1. Return implícito

Si el cuerpo es una única expresión, se puede escribir en una línea:

```js
const sumar = (a, b) => a + b;
```

#### 3.9.2. Un parámetro: paréntesis opcionales

```js
const cuadrado = n => n * n;
```

En web moderna son muy frecuentes, especialmente en callbacks (eventos, arrays, timers).

---

### 3.10. Funciones como “ciudadanos de primera clase”

En JavaScript:

* puedes pasar funciones como argumentos
* devolver funciones como resultado
* guardarlas en variables

Esto es fundamental y aparece en APIs del navegador constantemente (por ejemplo, `addEventListener`). ([developer.mozilla.org][5])

#### 3.10.1. Pasar funciones como parámetro (callback)

```js
function ejecutarAccion(accion) {
  console.log("Antes");
  accion();
  console.log("Después");
}

ejecutarAccion(function () {
  console.log("Acción ejecutada");
});
```

---

### 3.11. Closures

Un **closure** ocurre cuando una función “recuerda” variables de su entorno externo (scope léxico), incluso cuando ese entorno ya terminó. ([developer.mozilla.org][6])

#### 3.11.1. Ejemplo base: contador con estado privado

```js
function crearContador() {
  let cuenta = 0; // variable "privada"

  return function () {
    cuenta++;
    return cuenta;
  };
}

const contador = crearContador();

console.log(contador()); // 1
console.log(contador()); // 2
console.log(contador()); // 3
```

Qué está pasando:

* `crearContador()` crea `cuenta`
* devuelve una función interna
* esa función interna sigue accediendo a `cuenta`
* `cuenta` permanece viva porque la función devuelta la sigue usando

#### 3.11.2. Varios closures independientes

```js
const c1 = crearContador();
const c2 = crearContador();

console.log(c1()); // 1
console.log(c1()); // 2
console.log(c2()); // 1
```

Cada llamada a `crearContador()` crea “su propio” `cuenta`.

#### 3.11.3. Cierre aplicado a encapsulación (datos “privados”)

Ejemplo: encapsular un valor y exponer métodos:

```js
function crearPerfil(nombreInicial) {
  let nombre = nombreInicial;

  return {
    getNombre: function () {
      return nombre;
    },
    setNombre: function (nuevoNombre) {
      nombre = nuevoNombre;
    }
  };
}

const perfil = crearPerfil("Ana");
console.log(perfil.getNombre()); // Ana
perfil.setNombre("Lucía");
console.log(perfil.getNombre()); // Lucía
```

Este patrón:

* evita variables globales
* centraliza el estado
* controla cómo se modifica

---

### 3.12. Funciones, eventos y validación profesional en la web

En la web, el código no se ejecuta “de arriba abajo” como en una aplicación de consola. Gran parte de la lógica se ejecuta como respuesta a **eventos**.

Un **evento** es una acción que ocurre en el navegador: clic, teclado, envío de formulario, foco en un input, etc. ([developer.mozilla.org][2])

---

#### 3.12.1. Escuchar eventos con `addEventListener`

La forma estándar y moderna de reaccionar a eventos es:

```js
elemento.addEventListener("tipoEvento", funcion);
```

Ejemplo:

```js
const boton = document.querySelector("#btn");

boton.addEventListener("click", function () {
  console.log("Clic detectado");
});
```

`addEventListener` permite registrar manejadores de forma flexible y es el enfoque recomendado. ([developer.mozilla.org][5])

---

#### 3.12.2. La función manejadora y el objeto `event`

Cuando ocurre un evento, el navegador llama a tu función y puede pasarle un objeto con información del evento, normalmente llamado `event` (o `e`).

```js
boton.addEventListener("click", function (event) {
  console.log(event.type); // "click"
});
```

Ese objeto describe qué pasó (tipo de evento, elemento implicado, etc.). Es la forma “profesional” de escribir manejadores porque te permite tomar decisiones según el evento.

---

#### 3.12.3. Formularios: evento `submit` y `preventDefault`

Cuando un formulario se envía, el navegador realiza su acción por defecto: **enviar y recargar/navegar**.

Si quieres validar con JavaScript sin recargar, se usa:

```js
event.preventDefault();
```

Esto indica al navegador que no ejecute la acción por defecto. ([developer.mozilla.org][7])

Ejemplo:

```js
const form = document.querySelector("#formulario");

form.addEventListener("submit", function (event) {
  event.preventDefault();
  console.log("Formulario interceptado");
});
```

---

#### 3.12.4. `focus` y `blur` (validación por campo)

* `focus`: cuando un campo recibe el foco
* `blur`: cuando un campo pierde el foco

Son muy usados para validación progresiva y UX. ([es.javascript.info][8])

Ejemplo completo (mostrar error en blur, limpiar en focus):

```js
const inputEmail = document.querySelector("#email");
const errorEmail = document.querySelector("#errorEmail");

function validarEmailBasico() {
  const valor = inputEmail.value.trim();

  if (valor === "") {
    errorEmail.textContent = "El email es obligatorio";
    inputEmail.classList.add("invalido");
    return false;
  }

  errorEmail.textContent = "";
  inputEmail.classList.remove("invalido");
  return true;
}

inputEmail.addEventListener("blur", function () {
  validarEmailBasico(); // feedback (no bloquea)
});

inputEmail.addEventListener("focus", function () {
  errorEmail.textContent = "";
  inputEmail.classList.remove("invalido");
});
```

---

#### 3.12.5. Separar “feedback” y “control” (patrón real)

En formularios reales se suele seguir esta idea:

* En `blur` (o `input`): **avisar** (feedback), sin bloquear.
* En `submit`: **decidir** (control final), bloqueando si hay errores.

Esto evita:

* “atrapar” al usuario
* depender de si un blur ocurrió o no
* estados inconsistentes

---

#### 3.12.6. Validación fiable con varios campos (estructura escalable)

Estructura recomendada:

1. Una función por campo: valida y devuelve `true/false`
2. Una función de formulario: valida todos y enfoca el primer error
3. El `submit`: llama a la validación total y decide si enviar

Ejemplo:

```js
const form = document.querySelector("#form");
const nombre = document.querySelector("#nombre");
const email = document.querySelector("#email");
const edad = document.querySelector("#edad");

const errNombre = document.querySelector("#errNombre");
const errEmail = document.querySelector("#errEmail");
const errEdad = document.querySelector("#errEdad");

function validarNombre() {
  const v = nombre.value.trim();
  if (v.length < 3) {
    errNombre.textContent = "El nombre debe tener al menos 3 caracteres";
    return false;
  }
  errNombre.textContent = "";
  return true;
}

function validarEmail() {
  const v = email.value.trim();
  if (!v.includes("@") || !v.includes(".")) {
    errEmail.textContent = "Email no válido";
    return false;
  }
  errEmail.textContent = "";
  return true;
}

function validarEdad() {
  const v = Number(edad.value);
  if (Number.isNaN(v) || v < 0 || v > 120) {
    errEdad.textContent = "Edad no válida";
    return false;
  }
  errEdad.textContent = "";
  return true;
}

function validarFormulario() {
  const checks = [
    { ok: validarNombre(), el: nombre },
    { ok: validarEmail(), el: email },
    { ok: validarEdad(), el: edad }
  ];

  for (const c of checks) {
    if (!c.ok) {
      c.el.focus();
      if (typeof c.el.select === "function") c.el.select();
      return false;
    }
  }
  return true;
}

nombre.addEventListener("blur", validarNombre);
email.addEventListener("blur", validarEmail);
edad.addEventListener("blur", validarEdad);

form.addEventListener("submit", function (event) {
  if (!validarFormulario()) {
    event.preventDefault();
  }
});
```

Este patrón:

* es fácil de ampliar
* reutiliza funciones (blur y submit)
* no depende del orden de eventos
* es el comportamiento típico que se implementa en web “de verdad”

---

#### 3.12.7. Enviar el formulario después de `preventDefault`

Si interceptas el `submit` y todo está bien, puedes permitir el envío real de dos formas comunes:

1. **No llamar a `preventDefault()`** si es válido (lo más simple)
2. Llamar manualmente a `form.submit()` si previamente lo bloqueaste

En la práctica, lo más claro suele ser:

```js
form.addEventListener("submit", function (event) {
  const ok = validarFormulario();
  if (!ok) {
    event.preventDefault();
  }
});
```

El formulario se envía “solo” cuando `ok` es `true`.

---

### 3.13. Temporizadores en JavaScript: `setTimeout` y `clearTimeout`

En programación web es muy habitual **no ejecutar una acción inmediatamente**, sino hacerlo **después de un cierto tiempo** o **cancelarla si ocurre algo antes**.
Para ello, JavaScript proporciona **temporizadores**.

Los dos más importantes son:

* `setTimeout()`
* `clearTimeout()`

---

#### 3.13.1. `setTimeout()`

La función `setTimeout()` permite **ejecutar una función después de un tiempo determinado** (en milisegundos).

**Sintaxis básica:**

```js
setTimeout(funcion, tiempo);
```

* `funcion`: la función que se ejecutará
* `tiempo`: tiempo en milisegundos (1000 ms = 1 segundo)

Ejemplo sencillo:

```js
setTimeout(function () {
  console.log("Mensaje mostrado tras 1 segundo");
}, 1000);
```

En este caso:

* el mensaje **no aparece inmediatamente**
* aparece **1 segundo después**

---

#### 3.13.2. ¿Qué devuelve `setTimeout()`?

`setTimeout()` **devuelve un identificador del temporizador**.

Ese valor:

* **no es una función**
* **no es un objeto**
* es un **identificador interno** que el navegador usa para poder cancelar el temporizador

Ejemplo:

```js
const temporizador = setTimeout(function () {
  console.log("Hola");
}, 2000);
```

La variable `temporizador` guarda el **ID del temporizador**, y nos permitirá cancelarlo si lo necesitamos.

---

#### 3.13.3. `clearTimeout()`

La función `clearTimeout()` se utiliza para **cancelar un temporizador creado con `setTimeout()`**, antes de que se ejecute.

**Sintaxis:**

```js
clearTimeout(idTemporizador);
```

Ejemplo completo:

```js
const temporizador = setTimeout(function () {
  console.log("Este mensaje NO se mostrará");
}, 2000);

clearTimeout(temporizador);
```

En este caso:

* el temporizador se crea
* se cancela inmediatamente
* el mensaje **nunca llega a ejecutarse**

---

#### 3.13.4. Uso real: mostrar mensajes temporales

Un uso muy habitual es **mostrar un mensaje durante un tiempo limitado** (errores, avisos, confirmaciones).

Ejemplo: mostrar un mensaje de error durante 1 segundo

```js
const mensaje = document.querySelector("#mensaje");

function mostrarError(texto) {
  mensaje.textContent = texto;

  setTimeout(function () {
    mensaje.textContent = "";
  }, 1000);
}
```

Este código:

* muestra el error
* espera 1 segundo
* lo borra automáticamente

---

#### 3.13.5. Problema habitual: temporizadores encadenados

Si el usuario provoca el error varias veces seguidas (por ejemplo, pulsando rápido un botón), se pueden crear **varios temporizadores a la vez**, lo que genera comportamientos extraños.

Ejemplo del problema:

```js
function mostrarError(texto) {
  mensaje.textContent = texto;

  setTimeout(function () {
    mensaje.textContent = "";
  }, 1000);
}
```

Si esta función se llama varias veces:

* cada llamada crea un nuevo temporizador
* el mensaje puede desaparecer antes de lo esperado

---

#### 3.13.6. Solución profesional: cancelar el temporizador anterior

Para evitarlo, se guarda el ID del temporizador y se cancela antes de crear uno nuevo.

```js
let temporizador = null;

function limpiarError() {
  mensaje.textContent = "";
  temporizador = null;
}

function mostrarError(texto) {
  mensaje.textContent = texto;

  if (temporizador !== null) {
    clearTimeout(temporizador);
  }

  temporizador = setTimeout(limpiarError, 1000);
}
```

Qué ocurre aquí:

1. Se muestra el mensaje
2. Si ya había un temporizador activo:

   * se cancela con `clearTimeout`
3. Se crea un nuevo temporizador
4. Tras 1 segundo, se ejecuta `limpiarError`

Este patrón es **muy usado en código real**.

---

#### 3.13.7. Relación con funciones anónimas

En muchos ejemplos se usa una **función anónima** dentro de `setTimeout`:

```js
setTimeout(function () {
  mensaje.textContent = "";
}, 1000);
```

Pero también se puede usar una **función declarada**, lo que suele mejorar la legibilidad:

```js
function limpiarMensaje() {
  mensaje.textContent = "";
}

setTimeout(limpiarMensaje, 1000);
```

Ambas formas son correctas.
La elección depende de:

* claridad del código
* reutilización de la función
* complejidad del proyecto

---

#### 3.13.8. Uso típico en validaciones web

En aplicaciones web reales, `setTimeout` y `clearTimeout` se usan para:

* mostrar errores temporales
* mostrar mensajes de confirmación
* evitar saturar al usuario con mensajes
* mejorar la experiencia de usuario (UX)

Ejemplo conceptual:

```js
if (!datoValido) {
  mostrarError("Dato incorrecto");
  input.focus();
}
```

El mensaje aparece, el usuario corrige el error, y el mensaje desaparece automáticamente.

---

#### Idea clave final del apartado

En JavaScript, las funciones no se usan solo para “calcular cosas”. En programación web se usan sobre todo para:

* reaccionar a eventos
* validar entradas
* actualizar la interfaz
* estructurar el código de forma mantenible

Y por eso, dominar funciones (incluyendo closures y hoisting) ayuda a entender cómo funciona JavaScript en aplicaciones reales. ([developer.mozilla.org][6])

> `setTimeout` permite **posponer la ejecución** de una función.

> `clearTimeout` permite **cancelarla si ya no es necesaria**.

Este mecanismo, combinado con funciones, eventos y validación, es una de las herramientas más utilizadas en la programación web moderna.

---

[1]: https://javascript.info/function-basics?utm_source=chatgpt.com "Functions"
[2]: https://developer.mozilla.org/es/docs/Learn_web_development/Core/Scripting/Events?utm_source=chatgpt.com "Introducción a los eventos - Aprende desarrollo web | MDN"
[3]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions?utm_source=chatgpt.com "Functions - JavaScript - MDN Web Docs"
[4]: https://javascript.info/function-expressions?utm_source=chatgpt.com "Function expressions"
[5]: https://developer.mozilla.org/es/docs/Web/API/EventTarget/addEventListener?utm_source=chatgpt.com "element.addEventListener - API web | MDN"
[6]: https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Closures?utm_source=chatgpt.com "Closures - JavaScript - MDN Web Docs"
[7]: https://developer.mozilla.org/en-US/docs/Web/API/Event/preventDefault?utm_source=chatgpt.com "Event: preventDefault() method - Web APIs - MDN Web Docs"
[8]: https://es.javascript.info/focus-blur?utm_source=chatgpt.com "Enfocado: enfoque/desenfoque"
