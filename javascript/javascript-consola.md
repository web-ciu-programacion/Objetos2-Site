# Consola para probar código Javascript

volver a [JavaScript](./javascript-intro.md)

<br/>

## Román presenta ...
(... con algo de colaboración de Carlos ...)   
la consola para probar código JavaScript. Es como un micro-unit-test-library, para código sencillo JavaScript. Y anda mejor que el es6console :D.

<br/>

## Instalación
Está en el [repo de ejemplos](https://github.com/obj2-material/javascript-dom), en una carpeta `consola`.

Se la bajan a una carpeta de su disco, listo.

<br/>

## Preparación de un test
Los archivos `consola.html` y `consola.js` son fijos. Para probar cierto código, hay que poner
* el código a testear en el archivo `codigo-a-testear.js`. Acá se puede poner cualquier cosa: definición de clases, objetos que no son instancias, funciones, variables. Cualquier cosa.
* los tests en `tests.js`.

Todo esto tiene que estar en la misma carpeta.

<br/>

En el `tests.js` se definen los objetos que forman el caso de testeo, y después hay que definir una función que se llame `mostrarResultados()`. El nombre tiene que ser exactamente ese.

Adentro de esa función, básicamente le hablan a un objeto `c`, que es la consola, que entiende 4 mensajes
* `eval`, evalúa una expresión sin mostrar ni validar nada. 
* `test`, con dos parámetros, resultado esperado y expresión. El mismo orden que p.ej. JUnit. 
* `show`, evalúa una expresión y muestra el resultado. Si la expresión es un objeto, muestra algo similar a lo que hacía Wollok, la estructura de los atributos.
* `showText`, muestra un String, *sin evaluarlo*. Por eso es distinto al `show`. P.ej. si `pepita` es un objeto que tiene un solo atributo llamado `_energia`, entonces `show("pepita")` va a mostrar algo como `pepita = {"_energia":200}`, mientras que `showText("pepita")` va a mostrar `pepita`.

En `eval`, `test` y `show`, las expresiones se pasan como Strings.

<br/>

En la instalación hay un ejemplo que testea la clase `Golondrina`.

<br/>

## Ejecución 
Más fácil imposible: se abre `consola.html` sobre un browser. Muestra el detalle de lo que se muestra (`show`), lo que se ejecuta (`eval`) y los tests (`test`). Lo que sigue es el resultado de los tests de ejemplo.

```
SHOW pepita = {"_energia":200}
pepita.comer(30)
pepita.volar(80)
TEST pepita.energia() = 230  -->  Sí
TEST pepita.estaFeliz() = false  -->  Sí

SHOW juanita = {"_energia":40}
juanita.comer(8)
TEST juanita.energia() = 72  -->  Sí
TEST juanita.estaFeliz() = true  -->  Sí
juanita.volar(50)
TEST juanita.energia() = 13  -->  No, 12
TEST juanita.estaFeliz() = false  -->  Sí
juanita.comer(400)
SHOW juanita.energia() = 1612
```

Qué podemos ver acá:
* Las líneas que empiezan con `SHOW` corresponden a los usos de `c.show("expresion")` en el test. Se muestra la expresión, un signo `=`, y después el resultado de la expresión.  
En este ejemplo, en la primer línea se ve que `pepita` es un objeto que tiene un atributo `_energia` con valor 200, y en la última que el resultado de `juanita.energia()` es 1612.
* Las líneas que empiezan con `TEST` corresponden a los usos de `c.test(valorEsperado, "expresion")` en el test. Se muestra la expresión, un `=`, el valor esperado, una flecha `-->`, y el resultado del test. Si el test es OK pone `Sí`. Caso contrario, pone `No, ` seguido del valor que da la expresión, que es distinto del esperado.
En el ejemplo, el primer test sobre `juanita.energia()` da el valor esperado de 72, mientras que el segundo da 12, distinto al valor esperado de 13.
* Las líneas que no empiezan ni con `SHOW` ni con `TEST` corresponden a los usos de `c.eval("expresion")`. Se muestra la expresión que se evaluó.

Se atajaron todos los errores que se nos ocurrió. Si ocurre un error durante la ejecución del test, va a aparecer algo de esta forma.
```
=================   ATENCION   =================
pepita.comerx(30)    -----  la evaluación cortó con error 
pepita.comerx is not a function
================================================
```

la segunda línea es el mensaje de error que da la evaluación en JavaScript.

<br/>

## ¡Qué buena está! ¿Cómo hicieron?
Tiramos los tips de los conceptos que se usan. El código se puede ver, es `consola.js`.
* Para evaluar una expresión que viene como String, la función `eval` que viene con JavaScript.
* Para que la implementación se mantenga sencilla, se definió un objeto para que lo maneje el test, y que va haciendo cada cosa que se le va pidiendo apenas se la piden. 
* Para mostrar varias líneas, se usó un `textarea` al que se le van agregando líneas separadas por `\n`.
* Para controlar los errores, un sencillo `try {...} catch (err) {...}`, parecido al de Java. Esto está en `innerSureEval`.
* Para poder poner un solo `try / catch`, cuando se usa `innerSureEval` se pasa una función que es lo que hay que hacer *después* de evaluar, si es que no hubo error. Es un uso sencillo de una técnica que se llama *continuation passing style* (o similares).

