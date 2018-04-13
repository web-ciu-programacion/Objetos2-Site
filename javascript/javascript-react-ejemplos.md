# Clases en JavaScript - ejemplos y ejercicios

volver a [JavaScript](./javascript-intro.md)

volver a [React](./javascript-react-indice.md)

<br>

<br/>

## Ejemplos
Están en la carpeta 
```
react
```
del [repositorio de ejemplos](https://github.com/obj2-material/javascript-dom).

No manejamos la división entre `plain-js` y `browser`, porque React se usa para generar páginas Web, es todo "browser".

<br>

En <span style="color: orange">`base`</span> están los archivos que se necesita incluir para aplicar la [receta de Carlos para trabajar con React](./javascript-react-receta-carlos.md).

<br>

En <span style="color: orange">`iniciales`</span> encontramos ejemplos muy sencillos del uso de React, similares a los del [módulo inicial de JavaScript](./javascript-dom-basics-ejemplos.md'). Cada ejemplo incluye el HTML y el JS, de acuerdo a lo que se indica en la [receta de Carlos](./javascript-react-receta-carlos.md).

1. `zeroth-example`   
  Un ejemplo trivial, no tiene nada dinámico. Sirve solamente para mostrar qué elementos se necesitan para tener una página andando sobre React.  
  El nombre es un homenaje a Isaac Asimov, respecto de su [zeroth law](https://en.wikipedia.org/wiki/Three_Laws_of_Robotics#Zeroth_Law_added), en castellano [Ley Cero](https://es.wikipedia.org/wiki/Ley_Cero).
  <p></p>

2. `first-example`  
  Un botón que modifica el contenido y estilo de un paragraph.  
  Se ve 
  - cómo se manejan los aspectos dinámicos usando el atributo `state` y el método `setState`, y
  - la definición de un método que responde a un evento.
  <p></p>

3. `second-example`  
  Variante del anterior en la que cambia un elemento entero, se cambia un botón por un paragraph.  
  Este ejemplo muestra que no es necesario manejarnos con p.ej. `none` y `block`. Directamente se decide qué elementos incluir, o no, en una página.  
  También se muestra que una expresión JSX puede asignarse a una constante, y que después se incluye esta constante en lo que devuelve `render()`. Podría ser una variable en lugar de constante.

<br/>

En <span style="color: orange">`ventas-aereas`</span> tenemos.
1. `aviones-vuelos`  
  La página que muestra información sobre aviones y vuelos, con la misma funcionalidad que la incluida en [el módulo sobre clases en JS](./javascript-clases-ejemplos.md), implementada sobre React.  
  Se incluye el dominio en un archivo fuente separado, `ventas-aereas-dominio.js`.
  <p></p>

2. `aviones-vuelos-design`
   Hola.


<br/>

## Ejercicios

<br/>

### Ejercicio 1. 
Implementar las clases necesarias para resolver los ejercicios que se indican de las [guías de Objetos 1](https://objetos1wollokunq.gitlab.io/material/#guides)  
- Guía 5 ejercicio 4: atención de animales.
- Guía 7 ejercicio 1: agregados a atención de animales.

Hacerlo en archivos .js, después probar en es6console.  

**Importante**  
si se hacen correcciones, después volcarlas a los .js que se guardan.

<br/>

### Ejercicio 2.
Implementar las siguientes extensiones al modelo de ventas aéreas

1. Poder decir si *un vuelo es relajado o no*. Se considera que un vuelo es relajado si la cabina del avión tiene más de 4 metros de alto, y tiene menos de 100 asientos disponibles para pasajeros.  
2. Saber el *peso máximo de un vuelo*, que es la suma de estos factores.
  - Peso del avión, dato que hay que agregar en el modelo de avión.
  - Peso de los pasajeros, que es el resultado de multiplicar la cantidad de pasajeros (o sea, de asientos ocupados) del vuelo por un peso standard definido por la IATA (Asociación Internacional de Transporte Aéreo).
  - Peso de la carga, que depende del tipo de vuelo.  
    Para vuelos normales, es la cantidad de pasajeros * 23 kg.  
    Para vuelos de carga, el peso de la carga (que debe indicarse para cada vuelo de carga) más 700 kg de equipamiento de seguridad.  
    Para vuelos charter, 5000 kg fijo.
  - Peso de la nafta, que es distancia a recorrer en kilómetros (que debe indicarse para cada vuelo) por el consumo en litros de nafta por kilómetro, que depende del avión.
  - Peso del equipamiento reglamentario, esto lo define la IATA siendo este valor igual para todos los vuelos.
3. Conocer el total de asientos libres para un destino, considerando todos los vuelos registrados en el `VueloStore`.

**Sugerencia**  
Definir un objeto `iata`, que puede no ser instancia de ninguna clase, que maneja los valores de peso standard de pasajero y de peso de equipamiento reglamentario de cada vuelo.

Este ejercicio también es para probar en es6console.com.

<br/>

### Ejercicio 3.
Realizar las siguientes extensiones a `golondrina-simple.html`

1. cambiar la clase `Golondrina` por la herencia incluyendo `GolondrinaGolosa` y `GolondrinaPensativa`. Que Pepita sea golosa y Juanita pensativa.
2. agregar a lo que se muestra para cada ave, si tiene ganas de cantar o no. Sugerencia: usar el operador ternario con esta estructura:  
```
 ...tieneGanasDeCantar... ? "Sí" : "No"
```

<br/>

### Ejercicio 4.
Realizar las siguientes extensiones a `ventas-aereas.html`

1. agregar en la tabla de vuelos, una columna donde se muestre el nombre del avión de cada vuelo.
2. hacer que solamente muestre los vuelos del avión elegido.
3. (de lujo) agregar alguna forma que "limpie" el avión elegido, mostrándose un cuadro vacío (o nada) arriba, y los vuelos de todos los aviones abajo.
