# Ejercicio propuesto - jarras de cerveza

volver a [ejemplos y ejercicios Arrays / Strings / Object Literals](./javascript-arrays-strings-object-literals-ejemplos.md)

volver a [JavaScript](./javascript-intro.md)

<br/>

El objetivo es armar una página que muestre información sobre algunas carpas que formaron parte de una Fiesta de la Cerveza, y algunos asistentes a la misma. 

Se parte de la siguiente información.
```
    const carpaRoja = {
        color: "Rojo", 
        marcas: ["Leffe", "Hoegaarden", "Staropramen"],
        visitantes: [
            {nombre: "Juan", jarras: 5}, {nombre: "Analía", jarras: 8}, 
            {nombre: "Luis", jarras: 1}, {nombre: "Julia" , jarras: 2}, 
            {nombre: "Carla", jarras: 1}, {nombre: "Mario", jarras: 4},
            {nombre: "Liz", jarras: 1}
        ]
    }
    const carpaAzul = {
        color: "Azul", 
        marcas: ["Hoegaarden", "Quilmes", "Staropramen", "Grolsch"],
        visitantes: [
            {nombre: "Juan", jarras: 2}, {nombre: "Julia" , jarras: 3}, 
            {nombre: "Lucia", jarras: 1}, {nombre: "Yolanda", jarras: 1},
            {nombre: "Anahí", jarras: 7}
        ]
    }
    const carpaVerde = {
        color: "Verde", 
        marcas: ["Carlsberg", "Grolsch", "Amstel"],
        visitantes: [
            {nombre: "Juan", jarras: 1}, {nombre: "Luis", jarras: 3}, 
            {nombre: "Carla", jarras: 5}, {nombre: "Lucas", jarras: 5}
        ]
    }
    const carpaVioleta = {
        color: "Violeta",
        marcas: ["Quilmes", "Palermo", "Brahma"],
        visitantes: [
            { nombre: "Juan", jarras: 1 }, { nombre: "Lucas", jarras: 2 },
            { nombre: "Anahí", jarras: 1 }, { nombre: "Osvaldo", jarras: 1 },
            { nombre: "Sergio", jarras: 1 }, { nombre: "Paula", jarras: 2 },
            { nombre: "Elvio", jarras: 1 }, { nombre: "Sol", jarras: 1 }
        ]
    }
    const fiesta = [carpaAzul, carpaRoja, carpaVioleta, carpaVerde]
```

Como se observa: cada carpa se identifica por su color, en cada carpa se pueden vender varias marcas de cerveza, y se registra por cada carpa, cada una de las personas que la visitó indicando cuántas jarras de cerveza compró. No se cuenta con la información.

## Requerimiento básico

Armar una página que incluya la siguente información

1. Información general de la fiesta
    - cantidad de carpas  
    - cantidad total de asistentes  
      **Atención con esto** si una persona fue a más de una carpa, hay que contarla una sola vez. Para esto puede servir la clase `Set` de Javascript, ver [la documentación](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set). Para obtener una única lista con los asistentes de todas las carpas, puede servir la función `flatten` incluida en la librería <span style="color: slateblue">Lodash</span>, ver [la documentación](https://lodash.com/docs/4.17.5#flatten).  
    - los colores de las carpas donde hay al menos una persona que compró 4 o más jarras (en el ejemplo, son las carpas roja, azul y verde).  
    - si Roque asistió a la fiesta (o sea, visitó al menos una carpa) o no.  
    - si Julia asistió a la fiesta (o sea, visitó al menos una carpa) o no.  
2. Información de cada carpa
    * color
    * cantidad de asistentes en total
    * lista de asistentes que compraron exactamente una jarra     
    * lista de asistentes que compraron más de una jarra
    * cantidad total de jarras vendidas.

Para esta versión básica, se recomienda armar cinco recuadros, uno para la información general, y uno para cada carpa.


## Mostrar datos de una sola carpa

Modificar la página para que, en lugar de un recuadro por cada carpa, haya una barra con cuatro botones, uno por cada carpa, y debajo de esta barra, el recuadro con la información de la carpa elegida.

En esta versión, se acepta una barra con cuatro botones fijos, uno por cada una de las cuatro carpas conocidas.

Se admiten dos variantes sobre qué mostrar al cargarse la página, antes de pulsar cualquiera de estos botones:  
- que muestre la información de la carpa roja
- que el recuadro con la información de la carpa no aparezca (`display: none`), activándolo (`display: block`) al elegirse cualquiera de las carpas.


## Incluir datos sobre Grolsch

Agregar a la página la siguiente información sobre la marca de cerveza *Grolsch*: 




