
## 2. Estructuras de control de flujo y repetitivas

Una vez sabemos **almacenar datos** y **operar con ellos**, el siguiente paso es aprender a **controlar el flujo de ejecución de un programa**.

Las **estructuras de control** permiten decidir:

* qué código se ejecuta
* cuándo se ejecuta
* cuántas veces se repite

En JavaScript, estas estructuras se dividen principalmente en:

* **estructuras condicionales** → tomar decisiones
* **estructuras repetitivas (bucles)** → repetir acciones

---

### 2.1. Estructuras condicionales

Las estructuras condicionales permiten ejecutar un bloque de código **solo si se cumple una condición**.

Una condición es una **expresión booleana**, es decir, una expresión que se evalúa como `true` o `false`.

---

#### 2.1.1. Condicional `if`

La estructura condicional más básica es `if`.

```js
if (condicion) {
  // código que se ejecuta si la condición es true
}
```

Si la condición se evalúa como `true`, el bloque se ejecuta.
Si es `false`, se ignora.

**Ejemplo:**

```js
const edad = 18;

if (edad >= 18) {
  console.log("Eres mayor de edad");
}
```

---

#### 2.1.2. `if ... else`

La estructura `if ... else` permite ejecutar **un bloque u otro**, dependiendo de la condición.

```js
if (condicion) {
  // código si true
} else {
  // código si false
}
```

**Ejemplo:**

```js
const edad = 17;

if (edad >= 18) {
  console.log("Eres mayor de edad");
} else {
  console.log("Eres menor de edad");
}
```

---

#### 2.1.3. `else if`

Cuando hay más de dos posibilidades, se pueden encadenar condiciones usando `else if`.

```js
if (condicion1) {
  // ...
} else if (condicion2) {
  // ...
} else {
  // ...
}
```

**Ejemplo:**

```js
const edad = 17;

if (edad >= 18) {
  console.log("Eres mayor de edad");
} else if (edad >= 16) {
  console.log("Eres casi mayor de edad");
} else {
  console.log("Eres menor de edad");
}
```

**Idea clave**

> El programa entra **solo en el primer bloque cuya condición sea verdadera**.

---

#### 2.1.4. Anidación de condicionales

Es posible escribir un `if` dentro de otro `if`.

```js
const edad = 17;
const tieneCarnet = true;

if (edad >= 18) {
  if (tieneCarnet) {
    console.log("Puedes conducir");
  } else {
    console.log("No puedes conducir");
  }
} else {
  console.log("No puedes conducir");
}
```

Aunque es válido, **un exceso de anidación dificulta la lectura**.

---

#### 2.1.5. Uso de operadores lógicos para mejorar la legibilidad

En muchos casos, se puede evitar la anidación usando operadores lógicos.

```js
const edad = 17;
const tieneCarnet = true;

if (edad >= 18 && tieneCarnet) {
  console.log("Puedes conducir");
} else {
  console.log("No puedes conducir");
}
```

Otra técnica habitual es **guardar el resultado de una condición en una variable**:

```js
const puedeConducir = edad >= 18 && tieneCarnet;

if (puedeConducir) {
  console.log("Puedes conducir");
} else {
  console.log("No puedes conducir");
}
```

Esto mejora la legibilidad del código.
Este tipo de mejora se conoce como **refactorización**.

---

#### 2.1.6. Uso de llaves `{ }`

Si un bloque contiene **una sola instrucción**, las llaves son opcionales:

```js
if (edad >= 18)
  console.log("Mayor de edad");
```

No obstante, **se recomienda usar siempre llaves**, especialmente al aprender, para evitar errores y mejorar la claridad.

---

### 2.2. Estructura `switch`

La estructura `switch` permite ejecutar diferentes bloques de código en función del valor de una expresión.

---

#### 2.2.1. Sintaxis básica

```js
switch (expresion) {
  case valor1:
    // código
    break;
  case valor2:
    // código
    break;
  default:
    // código
}
```

* `break` evita que se ejecuten los casos siguientes
* `default` es opcional y actúa como un `else`

---

#### 2.2.2. Ejemplo básico

```js
const dia = "lunes";

switch (dia) {
  case "lunes":
    console.log("Hoy es lunes");
    break;
  default:
    console.log("No es lunes");
}
```

---

#### 2.2.3. Ejemplo con valores numéricos

```js
const dia = new Date().getDay();

switch (dia) {
  case 0:
    console.log("Domingo");
    break;
  case 1:
    console.log("Lunes");
    break;
  case 2:
    console.log("Martes");
    break;
  default:
    console.log("Otro día");
}
```

---

#### 2.2.4. Agrupación de casos

Varios `case` pueden compartir el mismo bloque de código.

```js
switch (dia) {
  case 0:
  case 6:
    console.log("Fin de semana");
    break;
  default:
    console.log("Día laboral");
}
```

---

#### 2.2.5. Importancia de `break`

Si se omite `break`, el flujo continúa ejecutando los siguientes casos.

```js
// Ejemplo incorrecto
switch (dia) {
  case 2:
    console.log("Martes");
  case 3:
    console.log("Miércoles");
}
```

---

#### 2.2.6. `switch` vs `if`

Ambas estructuras pueden resolver los mismos problemas.

* `if` suele ser mejor para **rangos o condiciones complejas**
* `switch` es más claro cuando se compara **un único valor contra varios casos**

---

#### 2.2.7. Patrón `switch(true)`

Existe un patrón menos común:

```js
switch (true) {
  case edad >= 18 && edad < 25:
    console.log("Joven");
    break;
  case edad >= 25:
    console.log("Adulto");
    break;
}
```

Este patrón es válido, pero **menos legible**.
Se recomienda preferir `if / else if`.

---

### 2.3. Estructuras repetitivas (bucles)

Los bucles permiten **repetir un bloque de código varias veces**.

Cada repetición se denomina **iteración**.

---

#### 2.3.1. Bucle `while`

El bucle `while` se ejecuta **mientras una condición sea verdadera**.

```js
while (condicion) {
  // código
}
```

**Ejemplo:**

```js
let contador = 5;

while (contador > 0) {
  console.log(contador);
  contador--;
}
```

---

#### 2.3.2. Bucles infinitos

Si la condición nunca se vuelve falsa, el bucle será infinito:

```js
while (true) {
  console.log("Bucle infinito");
}
```

---

#### 2.3.3. `break` y `continue`

* `break` → sale del bucle
* `continue` → salta a la siguiente iteración

```js
while (contador > 0) {
  contador--;

  if (contador === 2) {
    break;
  }
}
```

```js
while (contador > 0) {
  contador--;

  if (contador % 2 === 0) {
    continue;
  }

  console.log(contador);
}
```

---

#### 2.3.4. Bucle `do...while`

El bucle `do...while` se ejecuta **al menos una vez**.

```js
do {
  // código
} while (condicion);
```

**Ejemplo:**

```js
let respuesta;

do {
  respuesta = confirm("¿Te gusta JavaScript?");
} while (respuesta);
```

---

#### 2.3.5. Bucle `for`

El bucle `for` es ideal cuando se conoce el número de iteraciones.

```js
for (inicializacion; condicion; actualizacion) {
  // código
}
```

**Ejemplo:**

```js
for (let i = 1; i <= 10; i++) {
  console.log(i);
}
```

---

#### 2.3.6. Incremento y decremento en bucles

```js
let i = 5;
i++; // 6
i--; // 4
```

Son formas abreviadas de:

```js
i = i + 1;
i = i - 1;
```

---

#### 2.3.7. Bucles anidados

Un bucle puede contener otro bucle:

```js
for (let i = 1; i <= 3; i++) {
  for (let j = 1; j <= 3; j++) {
    console.log(i + " x " + j);
  }
}
```

---

### 2.4. Comprobación de tipos y validación básica con `typeof`

En muchos programas reales es necesario **comprobar el tipo de un dato antes de utilizarlo**, especialmente cuando el valor puede variar o no está completamente bajo nuestro control.

JavaScript proporciona para ello el **operador `typeof`**.

---

#### 2.4.1. El operador `typeof`

El operador `typeof` devuelve una **cadena de texto** que indica el tipo del operando.

```js
const numero = 7;
typeof numero; // "number"
```

Puede utilizarse tanto con variables como con valores directos:

```js
typeof undefined;    // "undefined"
typeof true;         // "boolean"
typeof 42;           // "number"
typeof "Hola mundo"; // "string"
```

---

#### 2.4.2. El caso especial de `null`

Existe un valor especial en JavaScript: `null`.

Aunque representa un **valor nulo intencionado**, el operador `typeof` devuelve:

```js
typeof null; // "object"
```

Esto es un **error histórico del lenguaje** que no puede corregirse sin romper código existente.

Por este motivo, **`typeof` no debe usarse para comprobar `null`**.

La forma correcta de comprobarlo es mediante comparación estricta:

```js
const valor = null;

valor === null; // true
```

---

#### 2.4.3. ¿Qué significa `"object"`?

Cuando `typeof` devuelve `"object"`, indica que el valor es un **tipo complejo**.

Ejemplos:

```js
typeof {};        // "object"
typeof [];        // "object"
typeof null;      // "object" (caso especial)
```

Los objetos son un concepto central en JavaScript y se estudiarán en detalle más adelante.

---

#### 2.4.4. Uso de `typeof` con estructuras de control

El operador `typeof` es especialmente útil cuando se combina con **condicionales** para validar datos antes de usarlos.

Ejemplo:

```js
const edad = 42;

if (typeof edad === "number") {
  console.log("La edad es un número");
}
```

También se puede combinar con operadores lógicos:

```js
const edad = 42;

if (typeof edad === "number" && edad > 18) {
  console.log("Mayor de edad");
}
```

Este tipo de validaciones es muy habitual en programas reales, formularios y funciones reutilizables.

---

#### 2.4.5. Otra comprobación útil: `isNaN()`

Cuando se trabaja con números, es frecuente necesitar comprobar si un valor **no es un número válido**.

JavaScript proporciona la función `isNaN()`:

```js
isNaN(10);        // false
isNaN("hola");    // true
isNaN(Number("a")); // true
```

Un uso típico combinado con estructuras de control:

```js
const valor = Number("abc");

if (isNaN(valor)) {
  console.log("El valor no es un número válido");
}
```

---

### Idea final del apartado

> Las estructuras de control permiten **decidir y repetir**,
> y son la base de cualquier programa real.

> Antes de tomar decisiones o repetir acciones,
> es importante **comprobar que los datos son del tipo esperado**.
