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

En la documentación de Array, ver estos métodos: `map`, `filter`, `forEach`, `some`, `every`, `find`, `reduce`.

<br/>

## Strings
JavaScript incluye también una clase **`String`** con bastantes vitaminas. Los atributos y métodos se pueden consultar en la [documentación de Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String).

En JavaScript, un String <span style="color: indianred">**no**</span> está definido como un Array. En otras palabras: String no es subclase de Array, ni tienen ninguna superclase común (salvo alguna general tipo `Object`). Sí tienen polimorfismo para algunos métodos y atributos, p.ej. `includes`, `slice` y `length`. 
Los String <span style="color: indianred">**no**</span> soportan los métodos que reciben funciones, como `map` o `filter`.

En los ejemplos se muestran algunos de los mensajes que entienden los Strings.

<br/>

## Object Literals
JavaScript incluye una notación muy sencilla para definir registros. P.ej. esta línea
```
let notaJuanaMate = { 
    alumno: "Juana", 
    materia: "Matemática", 
    notasTrimestrales: [8,6,9] 
}
```
define un registro con tres campos: `alumno`, `materia` y `notasTrimestrales`.

Se accede a un campo usando la notación de puntos, p.ej. el valor de
```
notaJuanaMate.materia
```
es el String `"Matemática"`. La notación de puntos se puede combinar con la de Array, o con ella misma. Si definimos
```
let eventosDelDia = { 
    nota: notaJuanaMate, 
    almuerzo: { plato: "Milanesa", bebida: "Vino tinto"} 
}
```
entonces estas expresiones
```
notaJuanaMate.notasTrimestrales[1]
eventosDelDia.nota.alumno
eventosDelDia.almuerzo.plato
```
tienen como valor `6`, `"Juana"` y `"Milanesa"` respectivamente.

<br/>

### Objetos con atributos y métodos
Esta notación permite incluir *métodos* además de valores. O sea, esta notación nos permite definir **objetos**. Por eso el nombre de <span style="color: slateblue">*object literal*</span>.
Definamos una versión de `notaMateJuana` como objeto, incluyendo métodos
```
let notaJuanaMate = { 
    alumno: "Juana", 
    materia: "Matemática", 
    notasTrimestrales: [8,6,9],
    leFaltanNotas: function() { return this.notasTrimestrales.length < 3},
    aprobo: function() { 
        return !this.leFaltanNotas() 
            && this.notasTrimestrales.every(nota => nota >= 6)
            && (this.notasTrimestrales.filter(nota => nota == 6).length <= 1
    },
    mejorNota: function() { return this.notasTrimestrales.reduce(
        (maxi,nota) => Math.max(maxi,nota)
    ), 0},
    alumnoEnMayuscula: function() { return this.alumno.toUpperCase() }
}
```
La condición de aprobación es tener todas las notas, que todas sean 6 o más, y no tener más de un 6.

En esta notación, un método se define como un atributo, al que se asigna *una función* como valor. 

<br/>

Con esta definición, podemos evaluar
```
notaJuanaMate.aprobo()
notaJuanaMate.mejorNota()
notaJuanaMate.alumnoEnMayuscula()
```
obteniendo como resultado `true`, `9` y `"JUANA"` respectivamente.

Un detalle a notar: `notaJuanaMate` es un objeto que <span style="color: indianred">**no**</span> es instancia de ninguna clase.  
Moraleja: en JavaScript podemos mezclar (y de hecho se usa) objetos que son instancias de una clase, con objetos que contienen su propia definición (como el de este ejemplo).

<br/>

### Los registros y objetos son dinámicos
Si `notaJuanaMate` está definida, podemos evaluar esta asignación
```
notaJuanaMate.anio = 2017
notaJuanaMate.notasConAyudita() = function() { 
    return this.notasTrimestrales.map(n => (n == 10) : n ? n + 1)
}
```

Esto <span style="color: slateblue">*agrega*</span> un atributo y un método a `notaJuanaMate`. Si evaluamos ahora
```
notaJuanaMate.anio
notaJuanaMate.notasConAyudita()
```
vamos a obtener `2017` y `[9,7,10]` respectivamente.

<br/>

### El acceso a atributos no definidos es `undefined` -- **no** da error
El objeto al que llamamos `notaJuanaMate` no tiene un atributo llamado `curso`.
*A pesar de esto*, si evaluamos
```
notaJuanaMate.curso
```
<span style="color: indianred">**no**</span> se genera un error, sino que se obtiene 
```
undefined
```
como respuesta. 

JavaScript define un valor `undefined` que indica que lo que se está pidiendo no está definido. Este valor es distinto a `null`.   
Esto no está considerado como un error, sino como una característica. P.ej. con esta expresión
```
let elCurso = (notaJuanaMate.curso === undefined) 
                    ? "Curso por defecto" : notaJuanaMate.curso
```
estamos verificando si el objeto tiene definido un curso. Si está definido lo usamos, si no, usamos un valor por defecto.

Para funciones o métodos, hay que tener en cuenta lo siguiente. 
El objeto `notaJuanaMate` no define el método `promedio`.
El resultado de
```
notaJuanaMate.promedio
```
<span style="color: orange">**sin**</span> los paréntesis, es `undefined`. Si evaluamos
```
notaJuanaMate.promedio()
```
sí va a generarse un error, porque `undefined` no es una función (un método es una función), y solamente las funciones pueden evaluarse.  
El truco de evaluar el método sólo si está definido queda así:
```
let elPromedio = (notaJuanaMate.promedio === undefined) 
                    ? 7 : notaJuanaMate.promedio()
```
notar que la comparación se hace sin paréntesis, y la evaluación con.

<br/>

### Postdata - == vs ===, valores falsy y truthy
Estas notas terminan comentando dos cuestiones que son bastante usadas en el ambiente JavaScript, que surgen a partir del truco que comentamos para ver si un valor está o no definido.

1.
  En la comparación se usa `===`, no `==`. Los tres iguales, `===`, es la comparación por identidad. Los dos iguales, `==`, es la comparación por igualdad.

2.
  Hay una verificación más general para dar valores por defecto, que comprende `undefined`, también `null`, y también otros casos. Se aprovecha que para JavaScript todo valor tiene una correspondencia booleana, o sea que en una condición, cada valor "juega" como `true` o como `false`. 
  Esto es lo que en la jerga se conoce como *valores falsy y truthy*.

  Dejo un par de referencias para leer.  
  [artículo sobre comparaciones](https://www.sitepoint.com/javascript-truthy-falsy/)  
  [artículo sobre truco para valores default](http://adripofjavascript.com/blog/drips/truthy-and-falsy-values-in-javascript.html)



