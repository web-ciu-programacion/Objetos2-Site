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
                    { this.state.texto }
                </span></p>
                <button onClick={() => this.changeTextAndFont()}>React magic</button>
            </div>
        )
    }

    // función que reacciona al evento de apretar el botón
    changeTextAndFont() { 
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
            { this.state.texto }
        </span></p>
        <button onClick={() => this.changeTextAndFont()}>React magic</button>
    </div>
)
```

Esta notación **no** es HTML, aunque lo parece. Es una sintaxis que "viene con React" llamada JSX (vale googlear JSX). El método `render` está devolviendo el resultado de evaluar una *expresión JSX*.

Se pueden escribir tags como en HTML, cualquier tag. Va a haber diferencias en la definición de los atributos de un tag, veremos algunas en lo que sigue.

<br/>

### Código JavaScript dentro de una expresión JSX
Dentro de una expresión JSX se puede insertar código JavaScript (JS) poniéndolo entre llaves. En el ejemplo tenemos tres expresiones JS insertadas en el JSX:
* el estilo del span, cuyo valor es `theStyle`,
* el contenido del span, `this.state.texto`, y
* la función del `onClick`.

<br/>

### La notación JSX construye objetos
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

<br/>

### Se puede insertar código JS en distintos lugares de una expresión JSX
Las secciones JavaScript dentro de una expresión JSX pueden ir en **cualquier lado**: en un atributo (como el style del span), en el valor de un elemento (del span), o definiendo un elemento (el botón). También podrían definir una estructura que incluya varios elementos, veamos otra variante
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

## Actualización mediante el atributo `state`
En el `render`, el tamaño de fuente y el contenido del `span` están definidos en base al atributo `state` del componente, son `this.state.tamanioFuente` y `this.state.texto` respectivamente.  
Este atributo se inicializa en el constructor, donde dice (recordemos)
```
this.state = { texto: "Miren lo que va a pasar acá", tamanioFuente: "medium"}
```

El método que reacciona al evento modifica los componentes del `state`, usando el método `setState` que está definido en la clase `React.Component`. Recordemos
```
// función que reacciona al evento de apretar el botón
changeTextAndFont() { 
    this.setState({ texto: "Hello React", tamanioFuente: "25px" }) 
}
```
Esto **alcanza** para que cambien el texto y el tamaño cuando se pulsa el botón.

<br/>

### Cómo maneja React las actualizaciones
En una primera versión, podemos decir que React funciona así: cada vez que se modifica el atributo `state` **mediante el método `setState`**, React recalcula todo el HTML evaluando el método `render`. Después vuelca el HTML calculado al DOM de la página, haciendo los cambios necesarios (3).

Acá hay que tener en cuenta que React **corre en el browser**, todo esto pasa sin ir a ningún servidor. 

Comparando con cómo se actualiza una página manipulando directamente el DOM, hay dos cosas que en React no hace falta hacer: definir un id para cada elemento que tenga algo dinámico, y modificar los elementos usando `document.getElementById` cuando se reacciona a un evento.  
Trato de contarlo con una tabla

| Manipulando directamente el DOM | Usando React |
| ------------- | ------------- | 
| se definen `id` para los elementos dinámicos | se definen los aspectos dinámicos en JavaScript dentro del JSX, relacionándolos con el `state` |
| se modifican los elementos accediéndolos mediante `document.getElementById` | se usa `setState` , React se encarga de modificar el DOM |


<br/>

### OJO - usar `setState`
Volvemos a destacar que para que React reaccione, es necesario **usar `setState`** para modificar el atributo `state` del componente. Si p.ej. codificamos el método `changeTextAndFont` así
```
changeTextAndFont() { 
    this.state.texto = "Hello React"
    this.state.tamanioFuente = "25px" 
}
```
el atributo `state` va a cambiar, pero React no va a detectar el cambio, y por lo tanto la página no se va a modificar.

<br/>
 
## JSX - detalles a tener en cuenta
Destacamos varias cuestiones que en JSX se manejan distinto que si se escribiera HTML.

<br/>

### Doble-llave en las definiciones de `style`
Dos de ellas tienen que ver con el atributo `style`, o sea, con la inclusión de CSS dentro de una expresión JSX.  
Recordemos que definimos
```
const theStyle = { fontSize: this.state.tamanioFuente }
```
y después incluimos esto
```
<span style={ theStyle }>
```
en una expresión JSX dentro del `render`. 
Notamos que el código JavaScript que queremos insertar es un object literal, que se define entre llaves. Entonces, si queremos definir el estilo directamente dentro de JSX, evitándonos la definición de la constante, tenemos que poner **dos** llaves: la de afuera para indicar una sección de JavaScript dentro de JSX, la de adentro para definir el object literal. Queda así:
```
<span style={ { fontSize: this.state.tamanioFuente } }>
```
Si fuera un valor fijo, p.ej. `25px`, quedaría así:
```
<span style={ { fontSize: "25px" } }>
```
Esta doble-llave se ve seguido en el código JSX. Este es el primer detalle.

<br/>

### Nombres de propiedades CSS y de atributos HTML
Para hablar del segundo, comparemos el `span` que abrimos recién en JSX, el de valor fijo, con cómo lo pondríamos en HTML:
```
<span style="font-size: 25px">
```
La propiedad CSS se llama `font-size`. Peeeero lo que estamos definiendo en la expresión JSX es un object literal, y las claves en un object literal en JavaScript no pueden tener guiones. Definir **en JSX** algo así
```
<span style={ { font-size: "25px" } }>
```
daría un error, porque `font-size` no puede ser key en un object literal JavaScript.

Para evitar este problema, en la definición de propiedades CSS, se cambian los guiones por el camelCase. En el ejemplo,  `font-size` por `fontSize`.  
Esto para todas las propiedades, p.ej. `background-color` hay que ponerlo como `backgroundColor`, etc..

De paso, los nombres de eventos también pasan a camelCase en JSX, aunque en este caso no es por necesidad. En el `render`, vemos que en lugar de `onclick`, el evento se define como `onClick`.

<br/>

### Código que responde a un evento, el truco del `self`
Respecto del evento, otra cosa. El código que responde a cada evento **no** se define como String, sino como una expresión JavaScript. En el ejemplo, se define una array function anónima:
```
<button onClick={ () => this.changeTextAndFont() }>...</button>
```

Notar que es válido hacer referencias a `this`, que es el componente React.
Pero ¡OJO!, esta forma de usar `this` vale solamente porque se está definiendo una arrow function. Si se definiera una función normal, onda `function() { ... codigo ...}`, entonces el `this` dentro del código de la función es la misma función, deja de ser el componente React.   
Para evitar este problema, se usa "el truco del `self`". Es más fácil mostrarlo que contarlo:
```
const self = this
// ... y cuando se necesita ...
<button onClick={ function() { self.changeTextAndFont() } >...</button>
```
Con la definición de arriba, se crea una constante `self` que apunta al componente React. Eso se mantiene dentro de la función, por lo tanto `self` es el componente.  
Usar `self` como nombre es una convención, se puede usar cualquier nombre y va a andar. 

<br/>

### Conviene poner las expresiones JSX entre paréntesis
Fíjense en el código de arriba, en el método `render` la expresión JSX que se devuelve está entre paréntesis. Después, en las distintas variantes del `render` que presentamos, siempre que se arma una expresión JSX, se la encierra entre paréntesis.  
Esto es porque al definir expresiones JSX sin ponerles paréntesis, a veces (no siempre) tuve problemas.  
Por lo tanto, me acostumbré, y aconsejo que se acostumbren, a encerrar siempre (o al menos en principio) las expresiones JSX entre paréntesis.

<br/>

### Comentarios en JSX
Finalmente, cómo poner comentarios dentro de una expresión JSX. En mi (Carlos) experiencia, los comentarios HTML `<!-- ... -->` me causaron problemas. La que me anduvo siempre fue meter una expresión JavaScript que es un comentario. P.ej. 
```
<p>
    {/* pongo un span dentro del párrafo */}
    <span style={ theStyle }>
        { this.state.texto }
    </span>
</p>
```
Las llaves son para marcar JavaScript, adentro el `/* ... */` indica comentario.


-----------------------
(1)
Hay distintas formas de hacer `import` en JavaScript. Ver detalles en [la página sobre cuestiones técnicas de JavaScript](./javascript-tenicidades.md)

(2)
Puede tener sentido definir un componente React sin método `render`, si en lugar de extender directamente `React.Component`, extiende uno también hecho por nosotros que ya tiene la estructura del `render()`, y la subclase solamente completa detalles.

(3)
Por favor, no nos preocupemos por la performance. Pareciera que React es muy ineficiente, porque rearma toda la página aunque el cambio sea chico. Creo que React tiene esto en cuenta, verificar en la documentación.  
Cuando tengamos una página que reaccione en forma lenta, hablamos. Pero no antes.