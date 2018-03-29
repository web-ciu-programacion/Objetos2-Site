# Clases en JavaScript - ejemplos y ejercicios

volver a [JavaScript](./javascript-intro.md)

<br/>

## Ejemplos
Están en la carpeta 
```
classes-in-js
```
del [repositorio de ejemplos](https://github.com/obj2-material/javascript-dom).

En <span style="color: orange">`plain-js`</span> tenemos
1. `golondrina-basica.js`   
  Definición y uso de una clase sencilla en JavaScript.

2. `golondrina.js`  
  Extensión del ejemplo anterior. 
  - se definen varias subclases de Golondrina.
  - se incluye el template method `tieneGanasDeCantar()`, que usa al método abstracto `estaFeliz()`.
  - se define una clase `Entrenador` que puede interactuar con instancias de (subclases de la clase) `Golondrina`.
  - se define una clase `TamagotchiVolador`, cuyas instancias son polimórficas con las de `Golondrina` para los entrenadores.
  - se define un objeto `contadorComerVolar`, que también es polimórfico con tamagotchis voladores y golondrinas para los entrenadores.  
  <p></p>

3. `ventasAereas.js`  
  Implementación parcial del enunciado "Ventas aéreas", versión octubre 2017, que puede verse en la página de ejercicios.  
  Incluye el agregado de vuelos y aviones al VueloStore.  
  Se destaca el uso de objetos "sueltos" (que no son instancias de clase) para implementar las políticas de precio de pasaje, y la definición del registro `politicasDePrecio` para acceder a estas políticas.

<br/>

En <span style="color: orange">`browser`</span> tenemos.
1. `golondrina-simple.html`  
  Una página para interactuar con dos instancias de la clase `Golondrina`.  
  Primer ejemplo de definición de clases JavaScript en una página Web.

2. `golondrina-intermedio.html` y `golondrina-sofisticado.html`  
  Refinamientos de `golondrina-simple.html` que buscan evitar la repetición de código en las funciones que responden a los eventos.

3. `ventas-aereas.html` y `ventas-aereas-dominio.js`  
  Página que muestra información a partir del modelo de objetos de ventas aéreas.  
  Se separa la definición de las clases y objetos en un archivo aparte de extensión `.js`, que se incluye usando `<script src ...>` en el archivo HTML.

4. `monsters-objetos.html` y `monsters-dominio.js`  
  Reimplementación de la página que muestra información de bandas y discos, incluida como ejemplo de arrays y object literals, donde la base de información se define usando clases.  
  Incluye una forma interesante de agregar fácilmente las ventas de un disco en distintos países. Ver la inicialización de los discos.

5. `monsters-objetos-2.html`  
  Extensión del ejemplo anterior, incluyendo información sobre bandas, con el armado de recuadros complejos incluyendo información de cada disco de una banda, y una lista de bandas generada dinámicamente.  
  Sirve como ejemplo de los límites de la utilización de JavaScript "puro" para armar páginas con complejidad de visualización y/o interacción.

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
` ...tieneGanasDeCantar... ? "Sí" : "No"`

<br/>

### Ejercicio 4.
Realizar las siguientes extensiones a `ventas-aereas.html`

1. agregar en la tabla de vuelos, una columna donde se muestre el nombre del avión de cada vuelo.
2. hacer que solamente muestre los vuelos del avión elegido.
3. (de lujo) agregar alguna forma que "limpie" el avión elegido, mostrándose un cuadro vacío (o nada) arriba, y los vuelos de todos los aviones abajo.
