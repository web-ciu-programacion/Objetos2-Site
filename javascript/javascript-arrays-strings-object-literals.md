# Array, String, object literals

volver a [JavaScript](./javascript-intro.md)

<br/>

## Arrays

La implementación de 
<span style="color: orange">**Array**</span>
de JavaScript es muy potente. Los Arrays se usan muy extensivamente por todos lados.  
Los Array de JavaScript son fáciles de usar como los de Java, y potentes como los List de Java.

JavaScript define la clase Array, que tiene muchos (pero muchos) métodos. 
Ver el detalle en [la documentación de Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

<br/>

### Lo básico: definir y acceder a un elemento

Es muy fácil crear Arrays en JavaScript:
```
let numeritos = [5,8,21,2,9,16,8,18]
let arrayComplicado = [[3,5,9],[34,2,32],numeritos]
```
en este ejemplo, el segundo es un array de arrays.

Para acceder a un elemento se usa esta notación sencilla
```
numeritos[4]
arrayComplicado[2]
arrayComplicado[2][4]
```
Los arrays en JavaScript son de base 0, o sea que p.ej. `numeritos[4]` es el 5to elemento, no el 4to.
Por lo tanto, las tres expresiones de acá arriba devuelven respectivamente, 9, el array [5,8,21,2,9,16,8,18] (porque el tercer elemento del `arrayComplicado` es el array definido como `numeritos`, y otra vez 9.

<br/>

### Otros accesos, modificaciones

Mencionamos algunos métodos de acceso y modificación de un String. Para profundizar, ir a la documentación

Para obtener una subsección se usa `slice`
```
[5,8,21,2,9,16,8,18].slice(2,5)
```
devuelve [21,2,9]. 

Para agregar y quitar elementos hay tres formas. Sólo las mencionamos, ver cómo usarlas en la documentaçión.
- `unshift` y `shift`: pone / saca al principio.
- `push` y `pop`: pone / saca al final.
- `splice`: saca y/o pone en cualquier lugar.

Otro método de Array que conviene aprender es `join`.

<br/>

### Métodos que trabajan con funciones.

Al igual que en Java 8, Wollok, Scala y otros, los Arrays de JavaScript incluyen métodos que reciben una función por parámetro, y a partir de esa función permiten hacer distintos análisis y transformaciones sobre el array.

Dos de las más conocidas son `map` y `filter`. El resto verlo en la documentación u otras referencias, y en los ejemplos.

La función que se pasa a estos métodos se puede definir de distintas formas. Este ejemplo muestra tres formas de hacer lo mismo
```
function triple(n) { return n * 3}
[5,8,21,2,9,16,8,18].map(triple)
[5,8,21,2,9,16,8,18].map(function(n) { return n * 3})
[5,8,21,2,9,16,8,18].map((n) => n * 3)
```
En las últimas dos líneas, se están usando dos formas distintas de definir una <span style="color: slateblue">*función anónima*</span>; es anónima porque no tiene un nombre como `triple`.  
En el primer caso usamos la notación standard para definir una función en JavaScript: 
```
function(n) { return n * 3 }
```
Observar que la *única* diferencia la definición de la función con nombre `triple`, es que no está el nombre.  
La última versión usa una <span style="color: slateblue">*arrow function*</span>. Es así de fácil: los parámetros entre paréntesis, flecha, lo que devuelve sin necesidad de poner `return`.
Ver la [documentación de Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions), otras referencias en Internet, y los ejemplos.

En la documentación de Array, ver estos métodos: `map`, `filter`, `forEach`, `some`, `every`, `find`, `reduce`'.

<br/>

## Strings
JavaScript incluye también una clase **`String`** con bastantes vitaminas. Los atributos y métodos se pueden consultar en la [documentación de Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String).

En JavaScript, un String <span style="color: indianred">**no**</span> está definido como un Array. En otras palabras: String no es subclase de Array, ni tienen ninguna superclase común (salvo alguna general tipo `Object`). Sí tienen polimorfismo para algunos métodos y atributos, p.ej. `includes`, `slice` y `length`. 
Los String <span style="color: indianred">**no**</span> soportan los métodos que reciben funciones como `map` o `filter`.

En los ejemplos se muestran algunos de los mensajes que entienden los Strings.

<br/>

## Object Literals
JavaScript incluye una notación muy sencilla para definir registros. P.ej. esta línea
```
let notaJuanaMate = { alumno: "Juana", materia: "Matemática", notasTrimestrales: [8,6,9] }
```
define un registro con tres campos: `alumno`, `materia` y `notasTrimestrales`.