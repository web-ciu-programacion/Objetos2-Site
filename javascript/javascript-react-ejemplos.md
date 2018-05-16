# React - ejemplos y ejercicios

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
2. `first-example`  
  Un botón que modifica el contenido y estilo de un paragraph.  
  Se ve 
  - cómo se manejan los aspectos dinámicos usando el atributo `state` y el método `setState`, y
  - la definición de un método que responde a un evento.
3. `second-example`  
  Variante del anterior en la que cambia un elemento entero, se cambia un botón por un paragraph.  
  Este ejemplo muestra que no es necesario manejarnos con p.ej. `none` y `block`. Directamente se decide qué elementos incluir, o no, en una página.  
  También se muestra que una expresión JSX puede asignarse a una constante, y que después se incluye esta constante en lo que devuelve `render()`. Podría ser una variable en lugar de constante.

<br/>

En <span style="color: orange">`ventas-aereas`</span> tenemos.
1. `aviones-vuelos`  
  La página que muestra información sobre aviones y vuelos, con la misma funcionalidad que la incluida en [el módulo sobre clases en JS](./javascript-clases-ejemplos.md), implementada sobre React.  
  Se incluye el dominio en un archivo fuente separado, `ventas-aereas-dominio.js`.
2. `aviones-vuelos-design`  
   La misma página que `aviones-vuelos`, con dos métodos agregados en el componente para evitar repetir secciones muy parecidas en la definición del `render()`.  
   Se muestra que es sencillo generar elementos en forma dinámica. En este caso, en lugar de botones fijos para tres aviones bien conocidos, se arma un botón para cada avión que tenga el Store.
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
- agregar un tercer botón, que haga desaparecer los otros dos. Mejora: que el tercer botón alterne entre incluir los otros dos o no.

<br/>

### Ejercicio 2.
Implementar las siguientes variantes a la página de ventas aéreas

1. En la tabla de vuelos, agregar el nombre del avión en cada vuelo.  
1. En la información del avión elegido, agregar la altura de la cabina. Para esto hay que agregar, en la clase `Avion`, un método que devuelva este dato (el atributo está, falta el método).  
1. En la tabla de vuelos, agregar la política de venta de cada vuelo, "estricta", "anticipada" o "remate".  
Para esto, hay que agregar un método `nombreParaMostrar` a cada uno de los objetos que representan las políticas. También hay que agregar un método en `Vuelo` que devuelva la política.  
1. Invertir el orden en que se muestra la información, poniendo los vuelos arriba y el avión elegido abajo.  
1. Agregar una tabla abajo que muestre información sobre las ciudades. Para cada una, la cantidad de pasajeros que salieron de la ciudad, y la cantidad que llegaron. La información ya está en el Store, ver la clase `Ciudad` y el método `ciudades()` en el VueloStore.
1. Reemplazar el nombre del avión por un link o botón, y que elija el avión correspondiente al clickear en el nombre. Sacar los botones para elegir avión, ahora se eligen desde la tabla de vuelos.
1. Separar la generación de la tabla de vuelos en un componente aparte, como está hecho en `aviones-vuelos-design-2.js` para la información del avión.

### Ejercicio 3.
Contador
<br/>
  Mostrar un número, debajo del mismo colocar los siguientes botones: "+1", "-1", "*2", "reset" (vuelve a 0).
  El state puede tener un solo componente numero, que es el número que se está mostrando. Que arranque en 0.

### Ejercicio 4.
Nano-ruleta
<br/>
  Arriba de todo, el saldo del jugador, que es un número.
  Cuatro botones, "apostar 10 a negro", "apostar 50 a negro", "apostar 10 a rojo", "apostar 50 a rojo".
  Lo que se apuesta se resta del saldo y se suma a la apuesta actual. Se supone que no apuesta a rojo y negro en la misma apuesta,alcanza con acordarse a qué apostó ("rojo" o "negro") y cuánto.
  Mostar la apuesta actual, p.ej. "Apuesta actual: 70 al rojo"
  Abajo otros tres botones "salió rojo", "salió negro", "salió 0".
  ¿Qué pasa?
  - si sale lo que apostó, se suma al saldo el doble de la apuesta actual.
  - en cualquier caso, la apuesta actual queda en 0.

  Pensar qué hay que poner en el state (respuesta: cantidad apostada, color apostado, saldo).

  Armar la página.

  Chiche: que queden deshabilitados (prop isEnabled) los botones negro si está apostando a rojo, o rojo si está apostando a negro.

### Ejercicio 5.
Interface de Golondrina
<br/>
  Implementar la clase Golondrina con energia(), comer(gramos), volar(kms) y estaFeliz().
  Una golondrina está feliz si su energía está entre 50 y 120.
  Agregar un atributo _nombre y un método nombre(). El constructor que tome nombre y energía inicial.
  Vale robarse la implementación de /classes-in-js/browser/golondrina-simple.html, y agregar/modificar lo que se necesite.

  Armar una página que sea una lista de golondrinas, para cada una nombre, energía y si está feliz o no.
  En el último vale poner "Sí" o "No", un checkbox que esté tildado o no, o dos imágenes, una para "sí" y otra para "no".
  Inicializar la lista con cuatro golondrinas, nombres a elección.
  Vale que esta lista esté directamente en el state del componente. O sea, el componente nos va a hacer de "store".

  También vale que la clase Golondrina y el componente estén en el mismo archivo .js.

  Agregar un atributo al state que sea ultimaOperacion, un String. Por ahora que sea "Todavía no se hizo nada".
  Agregar abajo de la lista un recuadro que muestre state.ultimaOperacion.

  Agregar en cada fila de la tabla dos botones que sean "comer 10" y "volar 10".
  Al pulsar "comer 10", la golondrina correspondiente come 10 gramos, y state.ultimaOperacion se actualiza al String
  "XXX comió 10 gramos" donde XXX es el nombre de la golondrina.
  OJO hacerlo en este orden, primero la golondrina come, después se hace el setState.
  El botón "volar 10" lo mismo volando 10 kms.

  Agregar en cada fila un botón "comer n", que abra un recuadro con un formulario de esta facha
     Darle de comer a la golondrina XXX   (esto es un título)
     
     Gramos:  <acá va un campo de texto>

     Confirmar  /  Cancelar  (dos botones)
  Con "confirmar", se le da de comer a la golondrina, se hace setState de ultimaOperacion "XXX comió n gramos", y desaparece el formulario.
  Con "cancelar", solamente desaparece el formulario.

  Si no se hizo de entrada, que el formulario de "Comer n" sea un componente separado. 
  Como props debe recibir
  - la golondrina para poder hacer que coma
  - el componente principal, para decirle que no muestre más el formulario al terminar.

  Idem con un botón "volar n".

  Agregar un botón debajo de la tabla de "Agregar golondrina". Aparece un formulario abajo que pide nombre y energía inicial, y los botones confirmar / cancelar. Ahora state.ultimaOperacion debe ser "Se agregó la golondrina XXX".

  Chiches: 
  - que el recuadro de última operación no aparezca hasta que no se haga una operación.
  - validar que la cantidad que se da a comer / volar es un número positivo (vale robárselo de ventas-aereas-power, ventana de agregar un vuelo).
  - hacer una superclase común para los componentes "volar n" y "comer n"
  - hacer que el formulario de "agregar golondrina" aparezca solito en la pantalla. Para esto hay que agregar un componente Aplicacion, que muestre o bien la lista de golondrinas o bien el formulario de agregar golondrina. Mover el state con la lista de golondrinas y la última operación a la aplicación.

### Ejercicio 6.
<br/>
Listado de ciudades registradas, país y población. Del país, el código de 3 letras. 
  Pequeño agregado al modelo: agregar la población de una ciudad, que nazca en 0. Completar la población de cada ciudad en la inicialización del vueloStore.
  
  Para esto hay que crear un nuevo componente. Crear un nuevo fuente ventas-aereas-power-ciudades.  
  Hacer que el nuevo componente sea subclase de PantallaAplicacionVuelos.
  Recordar que para esto hay que poner
    const ventasAereasUtils = require('./ventas-aereas-power-utils')
  al principio del nuevo fuente.

  Colgar el nuevo componente como un botón más desde la pantalla inicial.  
  Para esto, hay que hacer los siguientes cambios en ventas-aereas-power.js: 
  - require del nuevo fuente.
  - const pantallas, agregar una nueva
  - clase AplicacionVuelos
    - agregar opción en el "switch" en el método render(). Olvidarse del setUltimaAccion, no hace falta 
      y lo veremos más adelante. Que solamente devuelva un JSX que instancie la clase que crearon.
    - agregar método mostrarListaCiudades(), análogo a p.ej. mostrarListaVuelos()

### Ejercicio 7.
Mover el modelo de ventas-aereas-power de browser a server, en etapas.
1. pasar los vuelos al server, y que InfoVuelos los levante del server.
  Esto hacerlo en el componentDidMount.
  En este get, no traer los vuelos, sí los totales que se muestran en la ficha de vuelo.
  Adaptar DetalleVuelo para que tome los datos en este formato.

1. pasar la consulta de pasajes de un vuelo al server, y que DetallePasajesVuelo tome esta info del server con un get.

1. pasar la venta de un pasaje al server, con un post /pasajes. Usar el número de vuelo como identificador.

1. pasar la consulta de un avión al server, agregar un id a cada avión.

1. listar qué más hay que hacer, y hacerlo.
