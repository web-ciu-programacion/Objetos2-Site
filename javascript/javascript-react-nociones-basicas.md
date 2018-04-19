volver a [JavaScript](./javascript-intro.md)

volver a [React](./javascript-react-indice.md)

<br>

# React - primeras nociones

## Elementos básicos en un fuente React

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
        // ver renderSinJsx() abajo
        // 
        // Los elementos dinámicos no necesitan id, lo que es dinámico
        // se expresa en JavaScript, es lo que está entre llaves.
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
        // al cambiar el state *usando setState*,
        // React se encarga solito de actualizar la pantalla
        this.setState({ texto: "Hello React", tamanioFuente: "25px" }) 
    }

ReactDOM.render(
    <FirstExample />,
    document.getElementById('reactPage')
);
```

