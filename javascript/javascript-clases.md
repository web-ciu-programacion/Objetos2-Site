# Definición de clases

volver a [JavaScript](./javascript-intro.md)

<br/>

En Javascript podemos usar la versión clásica de la Programación Orientada a Objetos: definir clases y crear instancias de las clases definidas.

El aspecto general de la definición de una clase en JavaScript es similar al de otros lenguajes, como Java, C# o Scala, con la particularidad que es particularmente **<span style={"color: dodgerblue"}>compacta</span>**: varios modificadores o indicaciones presentes en otros lenguajes, no aparecen en Javascript.  
Veamos la definición de una sencilla clase JavaScript, que incluye un atributo y tres métodos.  
```
class Golondrina {
  constructor() { this._energia = 0 }
  energia() { return this._energia }
  comer(gramos) { energia += gramos * 4 }
  volar(kms) { energia -= kms + 10 }
}
```

