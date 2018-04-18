volver a [JavaScript](./javascript-intro.md)

volver a [React](./javascript-react-indice.md)

<br>

# Receta para tener una página con React andando (de Carlos)

Va una receta para armar un entorno donde se pueda trabajar con React.  
Para editor recomiendo [Visual Studio Code](https://code.visualstudio.com/).

<br>

## Hacer una sola vez.

- Instalar **npm** desde [la página de NPM](https://www.npmjs.com/get-npm).
- Ejecutar `npm install browserify --global`.

<br>

## Hacer una vez por cada carpeta donde se quiera trabajar con React

- Copiar tres archivos que están en el repo de ejemplos, carpeta `react/base`.  
  Dos son fijos: `.gitignore` y `package.json`.  
  El tercero depende de tu sistema operativo: para Linux es `jspack.sh`, para Windows es `jspack.bat`.  
- Ejecutar `npm install`. Se va a crear una subcarpeta `node_modules`. Perfecto.  
**OJO** este paso requiere de conexión a Internet. No mucha, pero algo mínimamente estable tiene que haber.

<br>

## Organización de una página

Hay que tener dos archivos, un `.html` y un `.js`. Pueden tener el mismo nombre.  
Para lo que viene, supondremos `pirulito.html` y `pirulito.js`.

<br>

### El archivo HTML
En el `head`, no olvidarse de incorporar Bootstrap si es que se va a usar.  

El `body` debe incluir dos cosas:
1. un `div` con `id` que va a ser donde va a intervenir React, y 
2. el include del `.js`.

Para nuestro caso, podría ser así:  
```
  <div id="reactPage"></div>
  <script src="./pirulito_build.js"></script>
```

El código HTML que genere React va a ir dentro del elemento `reactPage`.

**OJO**  
Notar que no se está incorporando `pirulito.js`, sino `pirulito_build.js`. Si se va a trabajar como indica esta receta, siempre hay que agregar `_build` al nombre del archivo JS.

<br>

### El archivo JS
Al principio, hay que incorporar las librerías `react` y `react-dom`, usando `require`. Una forma sencilla es esta:

```
const React = require('react')
const ReactDOM = require('react-dom')
```

<br>

Hay que definir una clase que extienda de la clase `Component` que viene con React.  
Esa clase tiene que tener un método `render`. Lo que devuelva este método es lo que va a inyectar React en la página.

Va un ejemplo, lo más corto posible, de una clase como las que hay que definir.
```
class FirstExample extends React.Component { 
    render() {
        return (
            <h1>Esto lo puso React</h1>
        )
    }
}
```

<br>

Después de la definición de la clase, hay que avisarle a React que incorpore la clase que definimos en la página. Para esto se usa react-dom. Es más fácil explicarlo sobre el ejemplo:
```
ReactDOM.render(
    <FirstExample />,
    document.getElementById('reactPage')
);
```

El método `render` de `ReactDOM` es el que interviene sobre la página. Tiene dos argumentos. 
- El primero es el objeto React que genera el HTML a incorporar, en este caso una instancia de la clase que definimos.  
**OJO** no se pone `new FirstExample()`, hay que ponerlo como está acá arriba.
- El segundo es el elemento de la página donde se va a incorporar el código que genera React. Fíjense que el id es el que pusimos en el archivo `.html` al principio, obviamente tienen que coincidir. Puede ser `reactPage` (yo dejo siempre ese) o lo que sea, lo importante es que coincida lo que se pone en el HTML y en el JS.

<br>

## ¿Cómo hago para probar?
Hay que hacer un paso previo a mandar el HTML a un browser. Desde una consola de línea de comandos, usar `jspack` con el nombre del archivo `.js`. En nuestro caso.
```
jspack pirulito
```

Si termina sin error, debe generar el `pirulito_build.js` que estamos incorporando desde el HTML.

Si hay errores de sintaxis en el JS, el jspack va a terminar con error, indicando el número de línea donde está el problema.

**ATENTI**  
El `jspack` es, claramente, para Windows. Algún alma caritativa lo "traducirá" a Linux.

<br>

## El ejemplo andando

Lo tienen en el repo de ejemplo, carpeta `react/iniciales`. Se llama `zeroth-example`, están el HTML y el JS.
