volver a [JavaScript](./javascript-intro.md)

volver a [React](./javascript-react-indice.md)

<br>

# Componentes React - primeras nociones
En la [receta de Carlos](./javascript-react-receta-carlos.md), se cuenta cómo es la estructura general de un archivo fuente que define un componente React, cómo se arma una página HTML que va a incluir componentes React, y cómo se hace para probar. 

El objetivo de este documento es contar algunas cuestiones básicas respecto a cómo definir un componente React.

<br/>

## El ejemplo

Para armar una página usando React, vamos a definir un **componente**.
Un componente es una clase JavaScript que extiende la clase `Component` que viene con React.

Este es un ejemplo de un archivo React completo, que incluye la definición de un componente, y la indicación de dónde incorporarlo dentro de una página.  
Este mismo ejemplo está en el repo, es `react/iniciales/firstExample.js`. La versión del repo tiene algunos elementos adicionales.
```
const React = require('react')
const ReactDOM = require('react-dom')

class FirstExample extends React.Component { 
    constructor(props) { 
        super(props); 
        // el state incluye los aspectos dinámicos de la página
        this.state = { texto: "Miren lo que va a pasar acá", tamanioFuente: "medium"}
    }

    render() {
        const theStyle = { fontSize: this.state.tamanioFuente }
        // esto es una expresión JSX, parece HTML pero no lo es
        return (
            <div>
                <p><span style={ theStyle }>
                    {/*  Los elementos dinámicos no necesitan id, 
                         lo dinámico se expresa en JavaScript entre llaves */}
                    { this.state.texto }
                </span></p>
                <button onClick={() => this.changeTextAndFont()}>React magic</button>
            </div>
        )
    }

    // función que reacciona al evento de apretar el botón
    changeTextAndFont() { 
        // al cambiar el state *usando setState*,
        // React se encarga solito de actualizar la pantalla
        this.setState({ texto: "Hello React", tamanioFuente: "25px" }) 
    }
}

ReactDOM.render(
    <FirstExample />,
    document.getElementById('reactPage')
);
```

La parte del final, o sea la invocación a `ReactDOM.render`, está comentada en [la receta de Carlos](./javascript-react-receta-carlos.md).

Hablemos del resto.

<br/>

## Import de librerías
Las dos primeras líneas
```
const React = require('react')
const ReactDOM = require('react-dom')
```

son una forma (1) de hacer `import` en JavaScript. Lamentablemente en JavaScript hay que poner el nombre de la librería cada vez que se usa una clase, objeto, función o lo que sea que se importa, por eso hay que poner `React.Component`, no alcanza con hacer el import y después poner `Component`.

<br/>

## El método `render`, la notación JSX
Cuando se incluye una clase React en una página, el HTML que genera surge de lo que devuelve el método `render`. Por lo tanto, **hay que** definir el método `render` en cada componente React que definamos (2).

En el ejemplo, el valor de retorno del método se especifica así:
```
const theStyle = { fontSize: this.state.tamanioFuente }
return (
    <div>
        <p><span style={ theStyle }>
            {/*  Los elementos dinámicos no necesitan id, 
                 lo dinámico se expresa en JavaScript entre llaves */}
            { this.state.texto }
        </span></p>
        <button onClick={() => this.changeTextAndFont()}>React magic</button>
    </div>
)
```

Esta notación **no** es HTML, aunque lo parece. Es una sintaxis que "viene con React" llamada JSX (vale googlear JSX). El método `render` está devolviendo el resultado de evaluar una *expresión JSX*.

Se pueden escribir tags como en HTML, cualquier tag. Va a haber diferencias en la definición de los atributos de un tag, veremos algunas en lo que sigue.

Dentro de una expresión JSX se puede insertar código JavaScript (JS) poniéndolo entre llaves. En el ejemplo tenemos tres expresiones JS insertadas en el JSX:
* el estilo del span, cuyo valor es `theStyle`,
* el contenido del span, `this.state.texto`, y
* la función del `onClick`.

Es **importantísimo** entender que las expresiones JSX devuelven objetos JavaScript, la notación es una forma más cómoda de crear varios objetos relacionados. 
El JSX de arriba es **equivalente** a lo siguiente
``` 
return React.createElement(
    'div', null,
    React.createElement(
        'p', null,
        React.createElement( 'span', { style: theStyle }, this.state.texto )
    ),
    React.createElement(
        'button',
        { onClick: function onClick() { return self.changeTextAndFont(); } },
        'JS magic'
    )
);
```

Teniendo en cuenta esto, se entiende que con una expresión JSX podemos hacer lo mismo que con una JavaScript, en particular devolverla (lo que se hace en el `render`), o también p.ej. asignarla a una variable local o atributo. P.ej. otra forma de escribir el `render` en el ejemplo es:
```
const theStyle = { fontSize: this.state.tamanioFuente }
let boton = (<button onClick={() => this.changeTextAndFont()}>React magic</button>)
return (
    <div>
        <p><span style={ theStyle }>
            { this.state.texto }
        </span></p>
        { boton } 
    </div>
)
```

Acá vemos que las secciones JavaScript dentro de una expresión JSX pueden ir en **cualquier lado**: en un atributo (como el style del span), en el valor de un elemento (del span), o definiendo un elemento (el botón). También podrían definir una estructura que incluya varios elementos, veamos otra variante
```
const theStyle = { fontSize: this.state.tamanioFuente }
let texto = (
    <p><span style={ theStyle }>
        { this.state.texto }
    </span></p>
)
let boton = (<button onClick={() => this.changeTextAndFont()}>React magic</button>)
return (
    <div>
        { texto } 
        { boton } 
    </div>
)
```

<br/>

### JSX - dos detalles a tener en cuenta




-----------------------
(1)
Hay distintas formas de hacer `import` en JavaScript. Ver detalles en [la página sobre cuestiones técnicas de JavaScript](./javascript-tenicidades.md)

(2)
Puede tener sentido definir un componente React sin método `render`, si en lugar de extender directamente `React.Component`, extiende uno también hecho por nosotros que ya tiene la estructura del `render()`, y la subclase solamente completa detalles.

