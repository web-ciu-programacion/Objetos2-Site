volver a [JavaScript](./javascript-intro.md)

volver a [React](./javascript-react-indice.md)

<br>

# React - después de lo básico

No creo que tengamos tiempo de armar material escrito.  
Queremos al menos hacer una lista de los temas que vamos a ver. 
Esperamos poder incluir ejemplos en el repo. Ahí vamos.

* Agregar o quitar partes del DOM, formas de hacerlo específicas de React.
* Definición de métodos para expresiones JSX que se repiten.
* Organización de una página en varios componentes React.
* Centralizar el estado en el componente raíz.
* Manejo de datos ingresados por el usuario.
  Los tres secretos del form
    - Agregar una función onChange en cada input, que actualice el state.
    - Poner los botones fuera del form.
    - No hay submit, hay una función que responde al evento "se pulsó el botón 'confirmar'".  
      Esta función hace la acción de negocio y la navegación.  
      Los valores ingresados por el usuario **están en el state**, no se miran los input. 
    - (relacionado con lo que van a leer en Internet)   
    Por eso se dice que el state es la "single source of truth", lo que debe estar siempre actualizado, y de donde hay que leer los valores ingresados, es el state.

* Invocaciones a un servidor, al inicializar una página y después.
    - El pedido es asincrónico.
    - Queda definido un evento "llegó la respuesta al pedido".
    - Hay que suministrar una función que responda a ese evento. La información pedida llega como parámetro de la función. Lo que haya que hacer después de obtener la info, hay que ponerlo dentro de esa función.
    - Nombres para esta función:
        + "continuation": cómo debe *continuar* el procesamiento luego de obtenida la info, o
        + "callback": yo te llamo a vos para que lances un pedido, cuando te llegue la respuesta vos llamá (o sea, el llamado pasa a ser llamador, por eso *back*) a la función que te paso.

