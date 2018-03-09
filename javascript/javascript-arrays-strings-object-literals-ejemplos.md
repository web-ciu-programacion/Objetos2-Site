# Array, String, object literals - ejemplos y ejercicios

volver a [JavaScript](./javascript-intro.md)

<br/>

## Ejemplos
Están en la carpeta 
```
array-string-object-literal
```
del [repositorio de ejemplos](https://github.com/obj2-material/javascript-dom).

En <span style="color: orange">`plain-js`</span> tenemos
1. `array.js`   
  Tiene algunos ejemplos de uso de métodos de la clase `Array`, trabajando sobre un array de números.  
  Incluye: métodos que reciben funciones, agregado y eliminación de elementos, uso de `reduce`.

2. `objectLiterals.js`  
  Define algunos object literals y un array de objetos.
  Propone algunos ejercicios para ejercitar en el uso de arrays de objetos, en particular, métodos que usan funciones donde la función recibe un objeto.

<br/>

En <span style="color: orange">`browser`</span> tenemos tres ejemplos.
1. `traverseNames.js`  
  Caso sencillo de uso de arrays: se definen dos arrays, y se accede a sus elementos por índice.  
  Es un ejemplo muy conciso en el que se usa la idea de definir funciones (`nextPerson` y `previousPerson`) que reaccionan a los eventos, y otra función (`showCurrentPerson`) que actualiza los elementos de la página.

2. `palabras.js`  
  Se trabaja con arrays de Strings.  
  Se define una nueva serie de funciones, que analizan la información para calcular lo que hay que mostrar en la página. 
  En estas funciones se usan métodos de las clases `Array` y `String`.
  La función `mostrarEstadisticas`, que es la que actualiza la página, usa estas funciones de cálculo.

3. `monsters.js`  
  Se trabaja con arrays de registros, donde cada registro está definido como un object literal.  
  Tiene funciones de cálculo, en la que se analizan los arrays usando métodos de `Array` que miran cada registro.  
  En este ejemplo también mostramos la **integración** con 
  - `bootstrap`, una librería CSS
  - `lodash`, una librería básica de funciones JavaScript
  
<br/>

## Ejercicios

Próximamente
