#  Indentificando Functions y Scope

Identificar las funciones globales, locales, funciones de callback, expresions, statement, clousure, scope, contextos de ejecucion, que funciones forman parte de la pila de ejecucion (stack execution) y que funciones forman parte de la cola de eventos (event queue) .


### Función Global

```js
$(document).ready(function(){})
```
*** 

### Funciones Locales

```js
// Es una función anónima, vinculado al evento input.
$inputCard.on('input', function() {...}) 
function activeButton() {...} 
function desactiveButton() {...}
function longitud(input) {...}
function soloNumeros(input) {...}
function isValidCreditCard(numberCard) {...}

```
***
### Funciones Callback

> Las funciones _callback_ es pasar una función como parámetro de otra función.

```js
// 1. la función anónima pasa como parámetro de una evento (línea 14)
$inputCard.on('input', function() {
    isValidCreditCard($(this).val().trim());
});

// 2. la función longitud es parámetro de la función soloNumeros (línea 45)
var creditCardNumber = soloNumeros(longitud(numberCard));
```

***

### Function Statement

```js
function activeButton() {...} 
function desactiveButton() {...}
function longitud(input) {...}
function soloNumeros(input) {...}
function isValidCreditCard(numberCard) {...}
```
***

### Function Expression

> No se encontro ninguna función guardada dentro de una variable
***
### Closure

> Un closure es una función que es libre de variables, es decir, la función definida en el closure "recuerda" el entorno en el que se ha creado.

`desactiveButton()` y `activeButton()`, son funciones que no declara ninguna varibles, mas accede a los atributos del `document`

***
### Scope

> El scope es el alcance de una variable, puede ser de dos tipos, global y local. 

```js
function isValidCreditCard(numberCard) {
  // la variable creditCarNumber, solo vive en el entorno lexical de la función isValidCreditCard().
  var creditCardNumber = soloNumeros(longitu(numberCard));
  if (creditCardNumber !== undefined) {
    // Estas variables solo se encuentra en el entorno lexical de la condicional if.
    var arr = [];
    var sumaTotal = 0;
    .
    .
    .
  }
}   
```

```js
function soloNumeros(input) {
    // la variable regex solo vive en el entorno `soloNumeros`
    var regex = /^[0-9]+$/;
    if (regex.test(input)) {
      return input;
    }
  }
```

***

### Execution stack

> Es una estructura de datos que registra las llamadas a funciones, básicamente en qué parte del programa estamos.

1. `console.log()`
2. `$(document).ready()`
3. `isValidCreditCard()`
4. `soloNumeros()`
5. `longitud()`
6. `activeButton()`
7. `desactiveButton()`

*** 

### Event Queue

> contiene una cola de mensajes, que es una lista de mensajes a procesar y las funciones de devolución de llamada asociadas para ejecutar.

1. Event `input` vinculado a la variable `$inputCard`




