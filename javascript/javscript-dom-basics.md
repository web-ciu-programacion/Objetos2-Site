# Javascript y páginas Web

## JS, browsers, DOM

Cualquier browser decente sabe ejecutar código JS.
Este código puede acceder a, y modificar, un modelo de la página Web que se está mostrando. Este modelo se llama **DOM (Domain Object Model)**.  
De esta forma, se logran páginas con mucho dinamismo resuelto del lado del cliente. O sea, que no es necesario hacer llamadas HTTP para ejecutar código en un servidor y modificar lo que se muestra en el browser, esto se hace sin que ningún servidor se entere.

JS es un lenguaje potentísimo, y toda esa potencia se puede usar en el código que se ejecuta en el browser.

El **DOM** es un *modelo de objetos*. 
Se parte de una referencia global a la página, que se llama `document`. El `document` tiene atributos y métodos. Algunos devuelven otros objetos del dominio de la página (p.ej. elementos), que también son objetos con sus atributos y métodos.

En  
https://www.w3schools.com/js/js_htmldom.asp  
está explicado qué es el DOM. En las páginas siguientes del mismo sitio (ver la sección _JS HTML DOM_) se describe cómo acceder y manipular el DOM desde código JS. Algo vamos a ver en las secciones siguientes


## Cómo incluir código JS que accede y modifica una página
Para incluir código JS en una página, se usa el tag `script` de HTML. Dentro de este tag se puede p.ej. definir una función e invocarla. 
En esta página

```
<html>
<head>
    <title>First JS example</title>
    <script>
    function fillDemo() {
        document.getElementById("demo").innerHTML = "Hello JavaScript";
    }
    </script>
</head>
<body>
    <p>
    <span id="demo"></span>
    </p>

    <script>fillDemo()</script>
</body>
</html>
```

se está usando `script` dos veces: dentro del `head` se define una función, dentro del `body` se la invoca. El browser ejecuta la función mientras está procesando el `body` de la página.   
La asignación  
`document.getElementById("demo").innerHTML = "Hello JavaScript"`  
modifica el contenido del `span`, que es el elemento de la página al que se le puso `"demo"` como `id`. Este es un ejemplo de uso del DOM: accedemos a un elemento y lo podemos modificar. Más sobre el DOM en el link que pusimos arriba, y también en el anexo más abajo.

Veamos esta variante
```
<html>
<head>
    <title>First JS example</title>
    <script>
    function fillDemo() {
        document.getElementById("demo").innerHTML = "Hello JavaScript";
    }
    </script>
</head>
<body>
    <p>
    <span id="demo">Miren lo que va a pasar acá</span>
    </p>

    <button onClick="fillDemo()">JS magic</button>
</body>
</html>
```
ahora la función no se va a invocar cuando se cargue la página, sino cuando se pulse el botón.  
Por lo general, la activación del código JS de una página va a responder a un **evento**. En este caso, el evento es el pulsado del botón. Hay muchísimos eventos asociados a cada tag HTML, ver en la documentación y/o browsear.


<br/>

***

# Elementos iniciales del lenguaje JavaScript
Las **funciones** son uno de los elementos principales del lenguaje JavaScript. En el primer ejemplo se define una función `fillDemo()`, sin parámetros. Esta función se puede usar en cualquier lado de la página; vemos que se usa en el `<script>` que pusimos dentro del body.  
Dicho un poco más técnico: las funciones que se definen tienen como scope toda la página. 

En una página también podemos manejar **variables**. Veamos este ejemplo en el que le cambiamos el color a un texto al pulsar un botón.
```
<html>
<head>
    <title>Cambio de color</title>
    <script>
    var elColor = null  // empieza sin color definido
    function cambiaColor() {
        elColor = (elColor == "blue") ? "red" : "blue"
        document.getElementById("demo").style.color = elColor
    }
    </script>
</head>
<body>
    <p>
    <span id="demo">Hola</span>
    </p>

    <button onClick="cambiaColor()">Cambiar color</button>
</body>
</html>
```
De paso, dos detalles sobre el código en esta página
- Se usa el operador ternario, para conocerlo (o refrescar la memoria) puede verse  
https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Operadores/Conditional_Operator
- JavaScript maneja el valor `null`. Hay otra cosa parecida, pero no igual, que es `undefined`. Por ahora dejo dos links para los curiosos  
https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/null  
https://phpsblog.wordpress.com/2013/03/09/javascript-diferencia-entre-null-y-undefined/  
este es un tema para profundizar más adelante.  


## JavaScript y programación con objetos
El lenguaje JavaScript incluye las características principales de la **programación con objetos**.  
Como ya dijimos, el *DOM* es un modelo de objetos. Mediante `document` accedemos a una referencia a un objeto. A ese objeto le enviamos el mensaje `getElementById`, con la misma notación que p.ej. Java o C++:  
`document.getElementById("apellido")`.  
Esto nos devuelve otro objeto, que representa a un tag dentro de la página. Accedimos a atributos de este objeto, p.ej.  
`document.getElementById("apellido").innerHTML`.

*Comentario importante*:  
En la comunidad JavaScript se acostumbra acceder, e incluso modificar, atributos de un objeto sin necesidad de pasar por un método. Esto lo vimos p.ej. con los usos del atributo `innerHTML`.
Esto puede resultar chocante respecto de lo que viste en el primer curso de objetos. 
Con los objetos de la librería de JavaScript y el DOM, en principio conviene usarlos como vienen, para no salirse mucho de las prácticas de la comunidad. Con los objetos que defina cada uno, se puede elegir manejarse "como indica la teoría".


## Para lectores curiosos y/o ansiosos
Van dos comentarios rápidos de cosas que vamos a profundizar más adelante.

1. La librería JavaScript incluye una clase Array muy poderosa, que se usa como array y también como lista. Ver la documentación en  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array

2. JavaScript no hace chequeos de tipos antes de la ejecución, y no se declaran los tipos de los identificadores (variables, atributos, parámetros).  
Hay un "primito" llamado TypeScript, que sí incorpora chequeos de tipos.
Los curiosos pueden buscar en la red.

Va también un comentario de algo que es interesante, pero que no vamos a trabajar en esta introducción.
Es muy fácil definir funciones que esperen *una función* como parámetro. P.ej.  
`function aplicarDosVeces(fn,n) { return fn(fn(n)) }`  
Si tengo la función  
`function triple(n) { return n * 3 }`  
entonces al evaluar  
`aplicarDosVeces(triple,5)`  
devuelve 45, que es el resultado de aplicar dos veces la función `triple` a partir del valor inicial `5`.


<br/>

***

#  Anexo - algunas características del DOM
Estos son los objetos, atributos y métodos del DOM que se usan en el código JS de los ejemplos iniciales.  

- `document`  
  es una referencia global al modelo de la página.  

- `document.getElementById(id)`  
  devuelve una referencia al elemento con el `id` indicado.  
  P.ej. si tenemos una página con esta pinta
  ```
  <html>
    <head>
      <title>Detalle de una persona</title>
    </head>
    <body>
      <div id="nombre">Diego Armando</div>
      <div id="apellido" style="color: blue; margin-down: 5px">Maradona</div>
      <div id="direccion">Habana y Segurola</div>
      <h3>Hijos</h3>
        <table id="hijos">
          <thead>
            <tr><th>Nombre</th><th>Nacimiento</th></tr>
          </thead>
          <tbody>
            <tr><td>Dalma</td><td>1987</td></tr>
            <tr><td>Giannina</td><td>1989</td></tr>
          </tbody>
        </table>
    </body>
  </html>
  ```
  entonces mediante
  `document.getElementById("apellido")`.
  accedemos al segundo `div`, que es el elemento que lleva como id `apellido`.
  En la misma página, la expresión
  `document.getElementById("hijos")`
  es una referencia a la tabla, con toda su estructura.

- `element.innerHTML`  
  acceso al contenido de un elemento. Es de lectura y escritura.  
  Ejemplos sobre la página que describimos recién. 
  - La expresión  
    `document.getElementById("apellido").innerHTML`  
    devuelve `"Maradona"`, que es el contendio del `div` que tiene como id 
    `"apellido"`.
    Notar que no se incluyen los atributos, solamente el contenido.   
  - Si hacemos  
    `document.getElementById("apellido").innerHTML = "Caniggia"`  
    se modifica el contenido de ese elemento.

- `element.style`  
  referencia al estilo CSS de un elemento. Presenta un atributo para cada propiedad CSS, p.ej. `element.style.color` o `element.style.margin-down`.  
  Se puede usar para acceder al valor y también para modificarlo, como se explicó para `element.innerHTML`.  
  En la página que estamos usando de ejemplo, la expresión 
  `document.getElementById("apellido').style.color` devuelve `"blue"`.

- `document.createElement(tag)`  
  crea un elemento correspondiente al tag que se indica.
  P.ej. `let nuevaFila = document.createElement("tr")`.

- `element.appendChild(innerElement)`  
- agrega un hijo al elemento que recibe el mensaje. El parámetro es otro elemento, que pudo haber sido creado usando `document.createElement`.  
  P.ej. 
  ```
    let equipo = document.createElement("tr")
    // ... se completa la fila que representa al equipo ...
    document.getElementById("tablaDePosiciones").appendChild(equipo)
  ```


A partir del `document` se puede acceder a muchos otros atributos, métodos y otros objetos, relacionados con la página Web que se está mostrando. 
Consultar en los links que se indican en esta página y en otra documentación.
