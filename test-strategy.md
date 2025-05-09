# Estrategia de Pruebas – Juego “Adivina tu número”

## Objetivo

El objetivo fue probar el juego “Adivina tu número” desarrollado en HTML y JavaScript, y asegurar que funcionara correctamente al ser abierto desde el archivo `index.html`. Durante las pruebas encontré varios errores que impedían que el juego funcionara como se esperaba. Aquí detallo cada uno, junto con cómo los resolví.

---

## Errores encontrados y soluciones

### 1. Número aleatorio mal generado

**Qué pasaba:**  
El número aleatorio se generaba con `Math.random() * 10`, lo cual daba decimales entre 0 y 10.

**Solución:**  
Lo cambié por `Math.floor(Math.random() * 100) + 1` para que el número fuera un entero entre 1 y 100, como indica el juego.

---

### 2. No se mostraba si el número era mayor o menor

**Qué pasaba:**  
La línea `document.querySelector('lowOrHi')` no funcionaba porque olvidaron poner el punto (.) para seleccionar una clase.

**Solución:**  
Corregí a `document.querySelector('.lowOrHi')`.

---

### 3. El botón no respondía al hacer clic

**Qué pasaba:**  
Se usó `addeventListener` con una “e” minúscula, por lo que nunca se ejecutaba la función.

**Solución:**  
Corregí a `addEventListener`, que es la forma correcta.

---

### 4. Mensajes invertidos: decía que perdiste cuando ganabas

**Qué pasaba:**  
Cuando adivinabas el número correcto, el juego mostraba que habías perdido.

**Solución:**  
Inviertí el orden de los mensajes para que se muestre “¡Felicitaciones!” al ganar y “Perdiste” cuando se acaban los intentos.

---

### 5. Comparación incorrecta del número ingresado

**Qué pasaba:**  
El valor ingresado por el usuario no se convertía a número, así que aunque fuera correcto, la comparación fallaba.

**Solución:**  
Convertí el valor con `Number(guessField.value)` para que se compare bien.

---

### 6. El número no se regeneraba bien al reiniciar

**Qué pasaba:**  
Cuando se reiniciaba el juego, se usaba `Math.floor(Math.random()) + 1`, lo cual siempre daba 1.

**Solución:**  
Reemplacé la línea por `Math.floor(Math.random() * 100) + 1`.

---

### 7. El botón de “Comenzar de nuevo” no funcionaba

**Qué pasaba:**  
El mismo error de `addeventListener` ocurría aquí también.

**Solución:**  
Lo corregí a `addEventListener` y ahora el botón reinicia el juego sin problemas.

---

## Observaciones del líder del equipo

Siguiendo la recomendación del líder, abrí la **consola del navegador (F12)** mientras probaba. Ahí fue donde encontré errores como:

- `Uncaught TypeError: ... is not a function`
- `querySelector(...) is null`

Estos mensajes me ayudaron a identificar rápidamente las líneas que fallaban y a resolver los problemas uno por uno.

---

## Conclusión

Después de hacer estas correcciones, el juego ahora funciona correctamente: genera un número entre 1 y 100, da pistas si el número es mayor o menor, y permite reiniciar el juego. También se muestran bien los mensajes según si se gana o se pierde. Recomendación para el futuro: validar que el input sea un número y agregar soporte al presionar Enter, no solo con clic.

