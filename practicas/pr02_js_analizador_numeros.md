
# Práctica Apartado 2 – Analizador de números

### Estructuras de control, repetitivas y arrays básicos

**Repositorio:** `pr_ap02_js_analizador_numeros`

---

## Objetivo

Crear una página web que permita **analizar una serie de números introducidos por el usuario**, aplicando:

* estructuras de control (`if / else`)
* estructuras repetitivas (`for` o `while`)
* arrays básicos

Este tipo de lógica es muy habitual en validaciones y procesamiento de datos.

---

## Enunciado

Crea una página web con:

* un campo de texto donde el usuario introduzca **números separados por comas**
* un botón con el texto **“Analizar”**
* una zona donde se mostrarán los resultados o los mensajes de error (estos tienen que aparecer solo dos segundos y en rojo)

Ejemplo de entrada válida:

```
3, 5, -2, 10, 7
```

---

## 1️⃣ Conversión y validación (estructuras de control)

Al pulsar el botón:

1. El texto introducido debe convertirse en un **array** usando `split(",")`.
2. Debes recorrer el array y comprobar:

   * que no está vacío
   * que **todos los valores son números**

3. Si hay algún error:

   * se debe mostrar un mensaje en la web (en rojo, durante 2 segundos)
   * no se continuará con el análisis

---

## 2️⃣ Análisis de los números (estructuras repetitivas)

Una vez validado el array, debes recorrerlo y calcular:

* cantidad total de números
* cuántos son positivos
* cuántos son negativos
* cuántos son cero
* el número mayor
* el número menor

---

## 3️⃣ Mostrar resultados

En la web debe mostrarse claramente:

* la lista de números introducidos
* todos los resultados del análisis

La página **no debe recargarse** en ningún momento.

---

## Requisitos técnicos obligatorios

* Uso de:

  * `if / else`
  * al menos un bucle (`for` o `while`)
  * arrays básicos
* Los errores deben mostrarse en la web (no con `alert`)
* JavaScript en archivo externo
* Código organizado y legible

---

## Métodos permitidos (y necesarios)

```js
split(",")
Number()
isNaN()
length
```

---

## Entrega

* enlace al repositorio de GitHub
* enlace a la web publicada (GitHub Pages)

---

## Ayuda: Introducción breve a Arrays en JavaScript

En muchos programas no trabajamos con un único dato, sino con **varios valores relacionados** (por ejemplo, una lista de números).

Para eso, JavaScript utiliza los **arrays**.

---

### ¿Qué es un array?

Un array es una **lista ordenada de valores** almacenados en una sola variable.

Ejemplo:

```js
const numeros = [3, 5, -2, 10];
```

En este array:

* hay varios valores
* cada valor ocupa una posición
* las posiciones empiezan en **0**

---

### Acceso a los elementos

Cada elemento se accede indicando su posición (índice):

```js
numeros[0]; // 3
numeros[1]; // 5
numeros[2]; // -2
```

---

### Recorrer un array

La forma más habitual de recorrer un array es usando un bucle `for`:

```js
for (let i = 0; i < numeros.length; i++) {
  console.log(numeros[i]);
}
```

Esto permite procesar todos los valores uno a uno.

---

### Crear un array a partir de texto

Muchas veces los datos llegan como texto, por ejemplo:

```
3,5,-2,10
```

Podemos convertir ese texto en un array usando `split()`:

```js
const texto = "3,5,-2,10";
const partes = texto.split(",");
```

Resultado:

```js
["3", "5", "-2", "10"]
```

⚠️ Los valores siguen siendo texto, por lo que es necesario convertirlos a número usando `Number()`.

---

### Tabla resumen – Arrays básicos

| Concepto    | Ejemplo            | Explicación              |
| ----------- | ------------------ | ------------------------ |
| Crear array | `[1, 2, 3]`        | Lista de valores         |
| Acceso      | `array[0]`         | Primer elemento          |
| Longitud    | `array.length`     | Número de elementos      |
| Recorrer    | `for (...)`        | Procesar todos           |
| Desde texto | `texto.split(",")` | Crear array desde string |
| Conversión  | `Number(valor)`    | Pasar texto a número     |

---

### Idea clave

> **Un array es una lista de valores que se recorre con un bucle.**
