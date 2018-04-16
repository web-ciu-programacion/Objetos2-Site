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
   La misma página que `aviones-vuelos`, con dos métodos agregados en el componente para evitar repetir secciones muy parecidas en la definición del `render()`.  
   Se muestra que es sencillo generar elementos en forma dinámica. En este caso, en lugar de botones fijos para tres aviones bien conocidos, se arma un botón para cada avión que tenga el Store.
  <p></p>

3. `aviones-vuelos-design-2`  
   La misma página que `aviones-vuelos`, separando dos de las secciones de la página en clases aparte.  
   Se muestra la concentración de estado en el componente principal, y el acceso al mismo desde los otros componentes mediante los `props`. También que la definición de componentes propios lleva a una variante "potenciada" de HTML.

<br/>

## Ejercicios

<br/>

### Ejercicio 1. 
Implementar los siguientes agregados sobre el ejemplo `iniciales/first-example`. 
- que el texto del botón cambie a `"Ya está"` después de que se pulsa.
- agregar un segundo botón, que cambie el color (atributo `color` del style) a rojo.
- que el botón agregado en realidad vaya alternando el color entre negro y rojo. O sea, si el texto está en negro lo pase a rojo, y si está rojo que lo pase a negro.  
**Desafío**: alternar entre más de dos colores, p.ej. negro / rojo / azul / verde / marrón.
- que el texto del botón que cambia de color indique a qué color va a cambiar. P.ej. `"Cambiar a color rojo"`.

<br/>

### Ejercicio 2.
Implementar las siguientes variantes a la página de ventas aéreas

1. En la tabla de vuelos, agregar el nombre del avión en cada vuelo.  
1. En la información del avión elegido, agregar la altura de la cabina. Para esto hay que agregar, en la clase `Avion`, un método que devuelva este dato (el atributo está, falta el método).  
1. En la tabla de vuelos, agregar la política de venta de cada vuelo, "estricta", "anticipada" o "remate".  
Para esto, hay que agregar un método `nombreParaMostrar` a cada uno de los objetos que representan las políticas. También hay que agregar un método en `Vuelo` que devuelva la política.  
1. Invertir el orden en que se muestra la información, poniendo los vuelos arriba y el avión elegido abajo.  
1. Reemplazar el nombre del avión por un link o botón, y que elija el avión correspondiente al clickear en el nombre. Sacar los botones para elegir avión, ahora se eligen desde la tabla de vuelos.
1. Separar la generación de la tabla de vuelos en un componente aparte, como está hecho en `aviones-vuelos-design-2.js` para la información del avión.

