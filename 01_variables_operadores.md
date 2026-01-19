
## 1. Variables y operadores en JavaScript

Antes de empezar a programar de verdad en JavaScript, es necesario conocer **cómo se almacenan los datos** y **cómo se realizan operaciones con ellos**.
Para ello utilizamos **variables** y **operadores**.

---

### 1.1. ¿Qué es una variable?

Una **variable** es un espacio de memoria donde se almacena un dato para poder usarlo más tarde en el programa.

Ejemplo conceptual:

> “Guardo un valor con un nombre para poder reutilizarlo.”

---

### 1.2. Declaración de variables en JavaScript

En JavaScript moderno existen **tres formas** de declarar variables:

* `let`
* `const`
* `var` (obsoleto, se evita)

---

#### 1.2.1. `let`

Se utiliza para variables **cuyo valor puede cambiar**.

```js
let edad = 18;
edad = 19;
```

Características:

* el valor puede modificarse
* tiene **alcance de bloque** (`{ }`)
* es la forma habitual para variables “normales”

---

#### 1.2.2. `const`

Se utiliza para valores que **no deben cambiar**, o para ser más exactos, **no deben reasignarse**.

```js
const nombre = "Ana";
```

Si intentamos cambiarlo:

```js
nombre = "Luis"; // Error
```

**Importante: `const` y el tipo de dato**

`const` **no significa que el contenido sea inmutable**, sino que **la variable no puede apuntar a otra cosa distinta**.

**Ejemplo con un tipo primitivo (NO permitido)**

```js
const edad = 20;
edad = 21; // Error
```

En los tipos primitivos, cambiar el valor implica reasignar la variable, lo cual no está permitido con `const`.

**Ejemplo con un objeto (SÍ permitido parcialmente, para modificar su contenido)**

```js
const persona = { nombre: "Ana", edad: 20 };

persona.edad = 21;      // ✔ Permitido
persona.nombre = "Luis"; // ✔ Permitido
```

Pero esto **NO está permitido**:

```js
persona = { nombre: "Carlos", edad: 30 }; // Error
```

La referencia al objeto no puede cambiar.

---

#### 1.2.3. `var` (NO recomendado)

```js
var contador = 0;
```

Problemas de `var`:

* no respeta el alcance de bloque
* puede provocar errores difíciles de detectar
* es una forma antigua

👉 **No se recomienda usar `var` en JavaScript moderno**.

---

#### 1.2.4. ¿Qué debo usar entonces?

Regla práctica:

* Usar **`const` siempre que sea posible**
* Usar **`let` cuando el valor tenga que cambiar**
* Evitar **`var`**

---

### 1.3. Tipos de datos en JavaScript

JavaScript es un lenguaje **de tipado dinámico**, lo que significa que **no es necesario indicar el tipo** al declarar una variable.

Los tipos de datos pueden clasificarse en **primitivos** y **complejos**.

---

#### 1.3.1. Tipos de datos primitivos

Son valores simples que **no contienen otros datos**.

Los más usados son:

| Tipo        | Descripción                 |
| ----------- | --------------------------- |
| `Number`    | Números enteros y decimales |
| `String`    | Texto                       |
| `Boolean`   | Verdadero o falso           |
| `null`      | Valor nulo intencionado     |
| `undefined` | Variable sin valor asignado |

Ejemplos:

```js
let edad = 20;             // Number
let precio = 9.99;        // Number
let nombre = "Diego";     // String
let activo = true;        // Boolean
let vacio = null;         // null
let sinValor;             // undefined
```

---

#### 1.3.2. Tipos de datos complejos

Son estructuras que pueden **contener varios valores**.

Los más utilizados son:

| Tipo       | Descripción                         |
| ---------- | ----------------------------------- |
| `Object`   | Conjunto de propiedades clave-valor |
| `Array`    | Lista ordenada de valores           |
| `Function` | Bloque de código reutilizable       |

Ejemplos:

```js
const persona = {
  nombre: "Diego",
  edad: 40
};

const numeros = [1, 2, 3, 4];

function saludar() {
  console.log("Hola");
}
```

---

### 1.4. Ámbito de las variables (scope)

El **ámbito** de una variable indica **desde dónde se puede acceder a ella**.

---

#### 1.4.1. Variables globales

Una variable es **global** si se declara fuera de cualquier bloque o función.

```js
let contador = 0;

function incrementar() {
  contador++;
}
```

La variable `contador` es accesible desde cualquier parte del programa.

---

#### 1.4.2. Variables de bloque

Una variable es **de bloque** si se declara dentro de `{ }` usando `let` o `const`.

```js
if (true) {
  let mensaje = "Hola";
  console.log(mensaje); // ✔
}

console.log(mensaje); // ❌ Error
```

👉 Las variables de bloque **solo existen dentro del bloque donde se declaran**.

---

#### 1.4.3. Diferencia clave entre `let` y `var`

Mientras los modificadores `let` y `const` respetan el ámbito del bloque dónde es declarada la variable, `var` funciona de la siguiente manera:

* Si una variable se declara con **`var` fuera de cualquier función**, se comporta como una **variable global**.
* Si una variable se declara con **`var` dentro de una función**, su ámbito es **toda la función** (no solo el bloque donde se declara).
* Si una variable se declara con **`var` dentro de un bloque** (`if`, `for`, `while`, etc.), **NO actúa como variable de bloque**:

  * ignora el bloque
  * se comporta como si se hubiera declarado al inicio de la función (o como global si no hay función).

**Ejemplo comparativo**

```js
function ejemplo() {
  if (true) {
    var x = 10;
    let y = 20;
  }

  console.log(x); // ✔ 10
  console.log(y); // ❌ Error
}
```

* `x` existe en **toda la función**
* `y` solo existe dentro del bloque `if`

**Idea clave final**

> **`var`** solo distingue entre “dentro de función” y “fuera de función”.   
> **`let` y `const`** distinguen bloques.

---

### 1.5. Operadores en JavaScript

Los **operadores** permiten realizar operaciones con variables y valores.

---

#### 1.5.1. Operadores aritméticos

Se utilizan para cálculos numéricos.

| Operador | Significado    |
| -------- | -------------- |
| `+`      | Suma           |
| `-`      | Resta          |
| `*`      | Multiplicación |
| `/`      | División       |
| `%`      | Resto          |

**Ejemplos:**

```js
let a = 10;
let b = 3;

a + b; // 13
a - b; // 7
a * b; // 30
a / b; // 3.333...
a % b; // 1
```

---

#### 1.5.2. Operadores de incremento y decremento

Permiten aumentar o disminuir una variable numérica en **una unidad**.

| Operador | Significado     |
| -------- | --------------- |
| `++`     | Incrementa en 1 |
| `--`     | Decrementa en 1 |

Ejemplos:

```js
let contador = 0;

contador++; // contador vale 1
contador--; // contador vale 0
```

También pueden escribirse **antes** de la variable:

```js
++contador;
--contador;
```

**Prefijo y sufijo: diferencia importante...**

Los operadores `++` y `--` pueden usarse de dos formas:

* **Sufijo**: `variable++` o `variable--`
* **Prefijo**: `++variable` o `--variable`

La diferencia aparece **cuando el valor se usa dentro de una expresión**.

---

**¿Qué es una expresión?**

Una **expresión** es cualquier fragmento de código que **se evalúa** y produce **un valor**.

Es decir:

> una expresión es algo que JavaScript puede calcular y devolver un resultado.

**Ejemplos de expresiones:**

```js
5 + 3        // expresión → devuelve 8
contador    // expresión → devuelve el valor de contador
x > 10      // expresión → devuelve true o false
x++         // expresión → devuelve un valor
```

**Expresión vs instrucción**

* **Expresión**: devuelve un valor.
* **Instrucción**: indica a JavaScript qué hacer.

Ejemplo:

```js
let resultado = 5 + 3;
```

* `5 + 3` → **expresión**
* `let resultado = ...;` → **instrucción**

> **Si algo puede usarse donde se espera un valor, es una expresión.**

---

**Operador en forma sufija (`variable++`)**

* Primero se usa el valor actual
* Después se incrementa o decrementa

```js
let x = 5;
let y = x++;

console.log(x); // 6
console.log(y); // 5
```

Explicación:

1. `y` toma el valor original de `x` (5)
2. después `x` se incrementa a 6

**Operador en forma prefija (`++variable`)**

* Primero se incrementa o decrementa
* Después se usa el valor

```js
let x = 5;
let y = ++x;

console.log(x); // 6
console.log(y); // 6
```

Explicación:

1. `x` se incrementa primero
2. el nuevo valor (6) se asigna a `y`

**Cuando no hay expresión**

Si el operador se usa **solo**, el resultado final es el mismo:

```js
let contador = 0;

contador++;
++contador;
```

En ambos casos, `contador` se incremente en `1` y termina valiendo `2` al finalizar la ejecución de estas instrucciones.

---

### 1.6. Operador `+` con números y strings

El operador `+` tiene **dos comportamientos**:

#### Suma numérica

```js
10 + 5; // 15
```

#### Concatenación de strings

```js
"Hola " + "mundo"; // "Hola mundo"
```

⚠️ Mezcla de tipos:

```js
"Edad: " + 20; // "Edad: 20"
```

JavaScript convierte automáticamente el número a texto.

---

### 1.7. Operadores de asignación

Sirven para asignar valores a variables.

| Operador | Ejemplo  | Equivale a  |
| -------- | -------- | ----------- |
| `=`      | `x = 5`  | asigna      |
| `+=`     | `x += 2` | `x = x + 2` |
| `-=`     | `x -= 1` | `x = x - 1` |
| `*=`     | `x *= 3` | `x = x * 3` |
| `/=`     | `x /= 2` | `x = x / 2` |

Ejemplos:

```js
let contador = 0;
contador += 1;
contador += 1;
```

---

### 1.8. Operadores de comparación

Se utilizan para comparar valores y obtener un resultado booleano (`true` o `false`).

| Operador | Significado          |
| -------- | -------------------- |
| `>`      | mayor que            |
| `<`      | menor que            |
| `>=`     | mayor o igual        |
| `<=`     | menor o igual        |
| `==`     | igualdad no estricta |
| `===`    | igualdad estricta    |
| `!=`     | distinto             |
| `!==`    | distinto estricto    |

Ejemplos:

```js
10 > 5;      // true
5 === 5;     // true
5 === "5";   // false
5 == "5";    // true (no recomendable)
```

#### 1.8.1. `==` vs `===` (muy importante)

* `==` compara valores **con conversión automática**
* `===` compara **valor y tipo**

Ejemplo:

```js
5 == "5";   // true
5 === "5";  // false
```

👉 **Buena práctica**: usar siempre `===`.

---

### 1.9. Operadores lógicos

Se utilizan para combinar condiciones.

| Operador | Significado |
| -------- | ----------- |
| `&&`     | AND         |
| `\|\|`     | OR          |
| `!`      | NOT         |

Ejemplos:

```js
true && true;   // true
true && false;  // false

true || false;  // true

!true;          // false
```

---

### 1.10. Orden de prioridad de los operadores en JavaScript

Al igual que en matemáticas, JavaScript sigue un orden de prioridad. JavaScript evalúa primero los operadores **con mayor prioridad**, y después los de menor prioridad.

```js
let resultado = 10 + 5 * 2; // 20, porque primero se evalúa `5 * 2` y después se suma `10`.
let otro = (10 + 5) * 2;   // 30, poerque primero se evalúa la expresión de dentro del paréntesis y después se multiplica por `2`.
```

#### 1.10.1. Uso de paréntesis `( )`

Los **paréntesis** tienen la **máxima prioridad**.

Sirven para:

* cambiar el orden de evaluación
* hacer el código más claro

👉 **Regla importante**:
Si hay dudas, usa paréntesis.

#### 1.10.2. Tabla de prioridad

De mayor a menor prioridad:

1. **Paréntesis** `( )`
2. **Incremento / decremento** `++ y --`
3. **Multiplicación, división y resto** `*, / y %`
4. **Suma y resta** '+ y -`
5. **Operadores de comparación** `<, >, <=, >=, ==, !=, ===, !==`
6. **Operadores lógicos** `&&, || y !`
7. **Asignación** `=, +=, -=, *=, /=`

#### 1.10.3. Ejemplos evaluados paso a paso

```js
let x = 10 + 5 * 2;
```

Evaluación:

1. `5 * 2` → 10
2. `10 + 10` → 20

```js
let x = 10 > 5 && 3 < 1;
```

Evaluación:

1. `10 > 5` → `true`
2. `3 < 1` → `false`
3. `true && false` → `false`

```js
let x = false || true && false;
```

Evaluación:

1. `true && false` → `false`
2. `false || false` → `false`

```js
let x = (false || true) && false;
```

Evaluación:

1. `(false || true)` → `true`
2. `true && false` → `false`

---

#### 1.10.4. Operadores `&&` y `||` (detalle importante)

Además de la prioridad, estos operadores tienen **evaluación corta**:

* `&&`:

  * si la primera condición es `false`, no evalúa la siguiente

* `||`:

  * si la primera condición es `true`, no evalúa la siguiente

Ejemplo:

```js
false && algo(); // algo() no se ejecuta
true || algo();  // algo() no se ejecuta
```

#### 1.10.5. Reglas prácticas para recordar

* JavaScript **no evalúa de izquierda a derecha sin reglas**
* Multiplicación y división van antes que suma y resta
* Comparaciones van después de operaciones aritméticas
* `&&` va antes que `||`
* La asignación va casi siempre al final
* **Si hay dudas → usar paréntesis**

> **Si una expresión es difícil de leer, necesita paréntesis.**

---

### 1.11. Buenas prácticas iniciales

* Usar nombres de variables claros
* Evitar `var` y Priorizar `const` frente a `let`
* Usar siempre `===`
* Evitar mezclar números y strings sin intención`
* Escribir código legible y ordenado antes que "ingenioso"

---
