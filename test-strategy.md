# Estrategia de Pruebas (Test Strategy)

## Objetivo
Este documento describe la estrategia de pruebas utilizada para identificar y corregir errores en la implementación del juego "Adivina tu número". El propósito del juego es garantizar que funcione correctamente según los requerimientos establecidos.

## Casos de Prueba

### 1. Validación del Número Generado
**Descripción:** Verificar porque al ingresar un numero no mostraba nada
**Prueba:** Abrir la consola del navegador y revisar si daba algun
**Esperado:** Estaba mal escrito `guessSubmit.addeventListener('click', checkGuess);` asi tambien como 
`resetButton.addeventListener('click', resetGame);` el unico error era el `addEventListener`.
**Corrección aplicada:** Se modificó la generación del número con `guessSubmit.addEventListener('click', checkGuess);` y 
`resetButton.addEventListener('click', resetGame);`.

### 2. Validación del Número Generado
**Descripción:** Verifico que el número generado aleatoriamente sea un número entero entre 1 y 100.
**Prueba:** Abrir la consola del navegador y revisar el valor de `randomNumber`.
**Esperado:** El número debe estar en el rango [1,100] y ser un entero.
**Corrección aplicada:** Se modificó la generación del número con `Math.floor(Math.random() * 100) + 1;` Estaba mal aplicada la logica que 
solo generaba un 1.

### 3. Validación de Entrada del Usuario
**Descripción:** Verificar que el usuario solo pueda ingresar números enteros entre 1 y 100.
**Prueba:** Ingresar valores inválidos como letras, números negativos o fuera del rango.
**Esperado:** Mostrar una alerta y no aumentar el contador de intentos.
**Corrección aplicada:** Se agregó validación con `parseInt()` y `isNaN(userGuess)` para poder aceptar solo numeros enteros asi como que este
en el rango entre 1 y 100.

### 4. Mensajes de Pérdida y Victoria
**Descripción:** Verificar que los mensajes correctos se muestren al ganar o perder el juego.
**Prueba:** Intentar adivinar el número y alcanzar el límite de intentos.
**Esperado:**
  - Si acierta, mostrar "¡Felicitaciones!" en verde.
  - Si pierde tras 10 intentos, mostrar "!!!Pérdistes!!!" en rojo.
**Corrección aplicada:** Se corrigieron los colores y los textos de los mensajes lo cual estaba mal aplicado anteriormente.

### 5. Comparación del Número Ingresado
**Descripción:** Verificar que el juego indique correctamente si el número ingresado es mayor o menor que el número a adivinar.
**Prueba:** Ingresar números mayores y menores al número secreto.
**Esperado:** Mostrar "El número es mayor!" o "El número es menor!" en negro.
**Corrección aplicada:** Se corrigió la referencia a `lowOrHi` en `document.querySelector('.lowOrHi')` ya que sin el punto(.) generaba que buscaba alguna etiqueta pero ahora con el punto busca la clase a la referencia.

### 6. Reinicio del Juego
**Descripción:** Verificar que el juego se pueda reiniciar correctamente tras ganar o perder.
**Prueba:** Completar una partida y presionar el botón de reinicio.
**Esperado:**
  - Se limpia la interfaz.
  - Se genera un nuevo número aleatorio.
  - Se habilitan los campos de entrada y botón de envío.
**Corrección aplicada:** Se corrigió la lógica de `resetGame()` ya que lo unico corregido fue la `Math.floor(Math.random() * 100) + 1`, para que diera el numero correcto.

## Conclusión
Después de haber implementado las nuevas correcciones, el juego ahora cumple con los requisitos funcionales y es totalmente jugable sin errores visibles en la consola del navegador, ya que ese era el error que teniamos que no dejaba ni jugar.
