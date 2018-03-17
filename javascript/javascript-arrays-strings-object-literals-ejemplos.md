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

<br/>

### Listas y Strings
1. 
  Consideremos una lista de palabras, p.ej.  

```
const martin = [
    "Aquí", "me", "pongo", "a", "cantar", 
    "al", "compás", "de", "la", "vigüela", 
    "que", "al", "hombre", "que", "lo", "desvela", 
    "una", "pena", "extraordinaria", 
    "como", "el", "ave", "solitaria", 
    "sólo", "al", "cantar", "se", "consuela"]
const canterville = [
    "Yo", "era", "un", "hombre", "bueno", 
    "si", "hay", "alguien", "bueno", "en", "este", "lugar", 
    "pagué", "todas", "mis", "deudas", 
    "perdí", "mi", "oportunidad", "de", "amar"]

const comidas = ["puré", "milanesa", "empanada", "arroz", "fideos", "mayonesa"]
const generos = ["rock", "pop", "disco", "rap"]
```

  Construir funciones que permitan obtener, para una lista de palabras:

  - los que empiecen con "a" o con "A"
  - los que tengan, al menos, una "a" o "A"
  - los que tengan, al menos, dos "a" o "A"
  - si hay al menos una palabra, de más de una letra, que empieza y termina con la misma letra
  - la lista con las mismas palabras, todas al revés (p.ej. )
  - la primer palabra de más de 7 letras

  P.ej. el resultado de cada una de estas expresiones  

```
empiezanConA(comidas)
tienenA(comidas)
tienenAlMenosDosA(comidas)
hayCoincidenciaPrimeraUltima(comidas)
hayCoincidenciaPrimeraUltima(generos)
alReves(generos)
primerPalabraDeMasDe7Letras(comidas)
```
  
  debe ser, respectivamente,  
  `["arroz"]`,  
  `["milanesa", "empanada", "arroz", mayonesa"]`,  
  `["milanesa", "empanada", mayonesa"]`,  
  `false`,  
  `true`,  
  `["kcor", "pop", "ocsid", "par"]`,
  `"milanesa"`  

  <br/>

2. Construir una función que, dados una lista de números `ln` y un número `x`, devuelva una lista con dos listas, la primera con los elementos de `ln` que sean números menores o iguales a `x`, la segunda con los que sean mayores a `x`.  
  P.ej. `separarSegun([3,8,21,2,19,6,1,22,4],10)` debe devolver `[[3,8,2,6,1,4],[21,19,22]]`.
  <br/>

<!--  
3. Construir una función que, dados una lista `lln` donde cada elemento es, a su vez, una lista de números, y un número `x`, devuelva una lista con las listas en `lln` donde está `x`.
  P.ej. `listasDondeEsta([[1,2,3],[4,8,13],[71,4,5,9],[2,5,6,1]],4)` debe devolver `[[4,8,13],[71,4,5,9]]`.
  <br/>
4. Construir la función `repetir(str,n)` que devuelve un String consistente en `n` copias del String `str`.
  P.ej. `repetir("pepo", 4)` debe devolver `"pepopepopepopepo"`.

<br/>

### Object literals
Considerar listas de registros de lluvia, con año, ciudad y milímetros caídos. P.ej.
```
let centroBuenosAires = [
    {year: 1902, city: 'Chas', mm: 822}, {year: 1903, city: 'Chas', mm: 901},
    {year: 1904, city: 'Chas', mm: 940}, 
    {year: 1902, city: 'Newton', mm: 749}, {year: 1903, city: 'Newton', mm: 748}, 
    {year: 1903, city: 'Villanueva', mm: 951}, {year: 1905, city: 'Villanueva', mm: 922},
    {year: 1902, city: 'Gral. Belgrano', mm: 883}
    ]
let misiones = [
    {year: 1902, city: 'Oberá', mm: 2304}, {year: 1903, city: 'Oberá', mm: 1891},
    {year: 1902, city: 'Andresito', mm: 1504}
]
```
Armar funciones que permitan, para una lista de registros de lluvia

  - cuánto llovió en un año en una ciudad.
    P.ej. `cuantoLlovioEn(centroBuenosAires, "Newton", 1903)` debe devolver `748`.
  - si hay al menos un registro de una ciudad.
    P.ej. `hayDatosDe(centroBuenosAires, "Jeppener")` y `hayDatosDe(centroBuenosAires, "Villanueva")` deben devolver `false` y `true` respectivamente.
  - los registros, con todos los datos, que correspondan a una cantidad de milímetros llovidos mayor a un número dado.  
    P.ej. `registrosQueExceden(centroBuenosAires, 930)` debe devolver  
    `[{year: 1904, city: 'Chas', mm: 940}, {year: 1903, city: 'Villanueva', mm: 951}]`.
  - cuánto llovió en total en una ciudad, sumando todos los años para los que hay registro.
    P.ej. `totalLluvias(centroBuenosAires,"Newton")` debe devolver `1497`.
  - si una ciudad está bien regada, o sea, tiene al menos dos registros, y en cada uno llovió al menos 900 mm. En `centroBuenosAires`, la única ciudad bien regada es Villanueva.
  - el registro (con todos los datos) con la mayor cantidad de lluvia. Para `centroBuenosAires`, es `{year: 1903, city: 'Villanueva', mm: 951}`.
  - para qué años hay registro en una ciudad. 
    P.ej. para `centroBuenosAires` debe devolver `[1902, 1903, 1904, 1905]` (en cualquier orden).
  - los registros de un año con ciudad y mm.
    P.ej., `registrosDelAnio(centroBuenosAires,1902)` tiene que devolver
  `[{city: 'Chas', mm: 822}, {city: 'Newton', mm: 749}, {city: 'Villanueva', mm: 951}]`.
  - (difícil) el resultado de agregar registros de una ciudad con este formato  
    `agregarRegistros(centroBuenosAires, "Ranchos", [{year: 1902, mm: 1041}, {year: 1903, mm: 1054}])`.  
    Tip: ver `Object.assign`.
  - (aún más difícil) lo mismo pero con este formato  
    `agregarRegistros(centroBuenosAires, "Ranchos", 1902, 1041, 1903, 1054)`  
    (alterna año y mm).
    Ver cantidad variable de argumentos.  
    Una variante más fácil es  
    `agregarRegistros(centroBuenosAires, "Ranchos", [1902, 1041, 1903, 1054])`.
-->

### Página Web
Se describe en una página aparte: [Jarras de cerveza](./jarras-de-cerveza.md)

  