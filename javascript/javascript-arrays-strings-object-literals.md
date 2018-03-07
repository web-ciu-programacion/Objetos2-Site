# Elementos comunes de JavaScript

volver a [JavaScript](./javascript-intro.md)

<br/>

## Arrays

La implementación de 
<span style="color: orange">**Array**</span>
de JavaScript es muy potente. Los Arrays se usan muy extensivamente por todos lados.  
Los Array de JavaScript son fáciles de usar como los de Java, y potentes como los List de Java.

JavaScript define la clase Array, que tiene muchos (pero muchos) métodos. 
Ver el detalle en [la documentación de Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).


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


### Métodos que trabajan con funciones.

Al igual que en Java 8, Wollok, Scala y otros, los Arrays de JavaScript incluyen métodos que reciben una función por parámetro, y a partir de esa función permiten hacer distintos análisis y transformaciones sobre el array.

Dos de las más conocidas son `map` y `filter`.

La función que se pasa a estos métodos se puede definir de distintas formas. Veamos un ejemplo de varias formas de hacer lo mismo
```
function triple(n) { return n * 3}
[5,8,21,2,9,16,8,18].map(triple)
[5,8,21,2,9,16,8,18].map(function(n) { return n * 3})
[5,8,21,2,9,16,8,18].map((n) => n * 3)
```


<!--
Las formas de agregar y de quitar elementos son extrañas, hay que aprendérselas. Ver push, unshift, pop, shift, splice.
Los Array de JS entienden map, filter, forEach, some, every, y varios otros mensajes que llevan un bloque de código como parámetro. Para definir los bloques, se pueden usar array functions, una funcionalidad agregada en JS 2015. También se puede escribir una función. 
-->
