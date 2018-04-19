volver a [JavaScript](./javascript-intro.md)

<br>

# JavaScript - detalles técnicos

## Importantísima nota previa

Hay distintas formas de hacer *cualquier* cosa en JavaScript, para casi nada hay una sintaxis única.  
Leer documentación y código requiere de paciencia, y no perder de vista que lo que se está viendo puede ser una forma nueva de hacer algo que uno ya conoce, pero con otra sintaxis.

<br/>

## Import

Una forma sencilla de hacer import de una librería es usando `require`. Es la forma que usamos para incorporar React a nuestras páginas:
```
const React = require('react')
const ReactDOM = require('react-dom')
```

Esta forma de hacer import tiene dos características que no resultan simpáticas.

**La primera**:  
se está importando todo lo que exporta la librería, no se puede elegir qué cosas se importan. En cambio, en el import de Java, p.ej. 
```
import java.util.List;
```
se está indicando de que todo lo que exporta el package `java.util`, se está eligiendo importar solamente la clase `List`.  
Hay formas alternativas de incorporar librerías que permiten indicar qué componentes se importan. Buscar en la documentación.

**La segunda**:  
El import no incluye el alias sobre los elementos importados. Por lo tanto, para crear una subclase de la clase `Component` que exporta la librería `React`, hay que hacer
```
class FirstExample extends React.Component { 
    ...
}
```
Hay que poner `React.Component`, no alcanza con poner `Component`.

En cambio, si en un fuente Java se importa `java.util.ArrayList`, se puede crear una instancia (supongamos, una lista de Strings) poniendo simplemente
```
new ArrayList<String>()
```
No es necesario incluir el nombre del package, o sea poner `new java.util.ArrayList<String>()`.

No conocemos ninguna variante de import que evite la necesidad de poner el nombre de package en cada referencia a algo importado. Cualquier iluminación respecto de esto, será más que bienvenida.