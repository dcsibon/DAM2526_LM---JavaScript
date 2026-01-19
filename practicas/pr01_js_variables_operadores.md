
# Práctica Apartado 1 – Variables, operadores y eventos en JavaScript

**Repositorio:** `pr01_js_variables_operadores`

## Entrega

La práctica se entregará mediante:

* un **repositorio de GitHub**
* la **web publicada** (GitHub Pages)

En la entrega se indicará:

* enlace al repositorio
* enlace a la web publicada

---

## Normas generales

* El código JavaScript debe estar en **archivo(s) externo(s)**.
* El proyecto debe funcionar correctamente al abrir la web publicada.
* No se permite copiar/pegar soluciones completas de internet.
* El repositorio debe estar **ordenado**, con nombres claros y **commits descriptivos**.
* Todos los resultados deben mostrarse **en la web (DOM)**, no solo por consola.

---

## Objetivo de la práctica

Crear una única página web que permita ejecutar **cuatro apartados independientes**, cada uno relacionado con el uso de:

* variables
* operadores
* expresiones
* eventos
* manipulación básica del DOM

Cada apartado se ejecutará **al pulsar un botón**, mostrando su resultado en la propia página.

---

## Estructura obligatoria del proyecto

El proyecto debe contener, al menos, los siguientes archivos:

* `index.html`
* `app.js`
* `styles.css` (opcional, pero recomendado)

---

## Estructura obligatoria del HTML

En `index.html` deben existir **exactamente** las siguientes secciones, con sus IDs correspondientes:

* `btnA1` y `a1` → Apartado 1
* `btnA2` y `a2` → Apartado 2
* `btnA3` y `a3` → Apartado 3
* `btnA4` y `a4` → Apartado 4

Ejemplo de estructura mínima:

```html
<section>
  <h2>Apartado 1</h2>
  <button id="btnA1">Mostrar resultado</button>
  <div id="a1"></div>
</section>

<section>
  <h2>Apartado 2</h2>
  <button id="btnA2">Mostrar resultado</button>
  <div id="a2"></div>
</section>

<section>
  <h2>Apartado 3</h2>
  <button id="btnA3">Mostrar resultado</button>
  <div id="a3"></div>
</section>

<section>
  <h2>Apartado 4</h2>
  <button id="btnA4">Mostrar resultado</button>
  <div id="a4"></div>
</section>
```

---

## Funcionamiento general

* Al cargar la página **no debe mostrarse ningún resultado**.
* Cada apartado se ejecuta **solo** cuando el usuario pulsa su botón.
* Cada apartado debe mostrar su resultado **únicamente en su contenedor** (`a1`, `a2`, `a3`, `a4`).
* El código de cada apartado debe estar **claramente separado**, preferiblemente en funciones.

---

## Apartado 1 – Variables y operaciones básicas

Al pulsar el botón del **Apartado 1** se debe realizar lo siguiente:

1. Crear variables que representen:

   * un **precio**
   * una **cantidad**
2. Calcular un **total** mediante una operación aritmética.
3. Mostrar en `a1` un texto que indique:

   * el precio
   * la cantidad
   * el total calculado
4. Incrementar la cantidad en **una unidad** usando un operador de incremento.
5. Recalcular el total.
6. Mostrar también el nuevo resultado, diferenciando claramente:

   * el valor inicial
   * el valor tras el incremento

---

## Apartado 2 – Comparaciones y operadores lógicos

Al pulsar el botón del **Apartado 2** se debe:

1. Crear una variable `edad` con un valor numérico.
2. Crear una variable booleana que indique si la persona **tiene carnet**.
3. Comprobar si la persona es mayor de edad usando un operador de comparación.
4. Crear una expresión lógica que determine si **puede conducir**.
5. Mostrar en `a2`:

   * la edad
   * si es mayor de edad (`true` / `false`)
   * si tiene carnet (`true` / `false`)
   * el resultado final de si puede conducir

---

## Apartado 3 – Incremento, expresiones y prioridad de operadores

Al pulsar el botón del **Apartado 3** se debe:

1. Crear una variable `x` con valor inicial `5`.
2. Crear una variable `y` usando una expresión que incluya `x++`.
3. Mostrar en `a3`:

   * el valor de `x`
   * el valor de `y`
4. Reiniciar `x` a `5`.
5. Crear de nuevo `y`, esta vez usando una expresión con `++x`.
6. Mostrar los nuevos valores de `x` e `y`.
7. Crear una expresión que combine suma y multiplicación **sin paréntesis** y mostrar su resultado.
8. Crear otra expresión equivalente **con paréntesis** para obtener un resultado distinto y mostrarlo.

---

## Apartado 4 – Tipos de datos y conversión implícita

Al pulsar el botón del **Apartado 4** se debe:

1. Crear una variable de tipo **String**.
2. Crear una variable de tipo **Number**.
3. Concatenar ambas usando el operador `+`.
4. Mostrar en `a4`:

   * el valor resultante de la concatenación
   * el tipo del resultado utilizando `typeof`

---

## Requisitos finales

* Cada apartado debe funcionar de forma independiente.
* El código debe ser claro, legible y bien organizado.
* Los resultados deben mostrarse correctamente en la web.
* No se deben usar alertas para mostrar resultados finales.

---

## Objetivo didáctico

Con esta práctica se pretende que el alumnado afiance:

* el uso de variables (`let` / `const`)
* operadores aritméticos, lógicos y de comparación
* expresiones y prioridad de operadores
* eventos (`click`)
* manipulación básica del DOM

