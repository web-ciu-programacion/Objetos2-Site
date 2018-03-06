# Javascript y páginas Web - ejemplos y ejercicios

volver a [JavaScript](./javascript-intro.md)

<br/>

## Ejemplos
Están en la carpeta 
```
javascript-dom-basics
```
del [repositorio de ejemplos](https://github.com/obj2-material/javascript-dom).

En `plain-js` hay un archivo que define algunas funciones y las usa. 

En `browser` hay algunos ejemplos sencillos de definición de funciones y de modificación de una página usando el DOM. 
- en `simpleExample` la modificación se hace al cargarse la página.
- en `simpleExampleWithButton` y `simpleExampleDisappearingButton` se modifica el contenido y/o el estilo de un elemento, como respuesta al evento de pulsar un botón.
- en `cambiaColor` se alterna entre dos colores para un elemento.  
Se utiliza una variable para recordar cuál es el color actual.

<br/>

## Ejercicios

1.  
  Armar una página con un contador que muestre un valor y tres botones, que suman uno, restan uno, y multiplican por dos respectivamente, el valor que se muestra. Puede ser algo así  
  ![contador](images/contador.jpg "Contador")  
  
  Consejos
  - Usar una variable para mantener el valor actual, ver cómo está hecho en el ejemplo `cambiaColor`.
  - Definir una función para cada botón.  
        
  De lujo:

  - Definir una función *aparte* que *solamente* actualice el valor del elemento. Las funciones de cada botón llaman a esta. Usar el `onLoad` que se puede poner en el `body` para mostrar el valor inicial.
        
2.  
  Armar una página con un mensaje y botones que permitan cambiarle el tamaño de letra y el color. Puede ser algo así  
  ![cambia estilo](images/cambia-estilo.jpg "Cambia estilo")  

<!---
- Mensaje con botones para cambiar el tamaño de letra y el color (ponele 10,12,14 puntos, rojo, verde, azul).
- Ana, Beto, Clara. Para cada uno, un botón "entró" y otro "salió". Que muestre quiénes están. 
  Chiche: que deshabilite los botones que no tienen sentido.
- mover una "X" a la izquierda o a la derecha (también puede ser para arriba y para abajo, en una fuente monospaced).
  P.ej. transformar ----X----- en ---X------ o -----X---- .
-->



