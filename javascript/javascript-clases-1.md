# Definición de clases

volver a [JavaScript](./javascript-intro.md)

<br/>

En Javascript podemos usar la versión clásica de la Programación Orientada a Objetos: definir clases y crear instancias de las clases definidas.

El aspecto general de la definición de una clase en JavaScript es similar al de otros lenguajes, como Java, C# o Scala, con la particularidad que es particularmente <span style="color: dodgerblue">**compacta**</span>.  
Varios modificadores o indicaciones presentes en otros lenguajes, no aparecen en Javascript.  

En lo que sigue, vamos a mencionar algunas características que se pueden apreciar en un ejemplo sencillo.

<br/> 

<span style="font-size: 125%; color: palegreen">**Atención**</span>  
La notación que vamos a ver se introdujo en la versión 2015 de JavaScript, también llamada "ES6" o "EcmaScript 6".  
Por eso hay en la Web varias explicaciones de cómo definir clases en JavaScript con una notación distinta, bastante más oscura. Así es como había que hacer en las versiones anteriores de JavaScript, en particular en ES5.

<br/> 

# Una clase sencilla

Esta es la definición en JavaScript de una clase sencilla, que incluye un atributo y tres métodos.  
```
class Golondrina {
  constructor() { this._energia = 0 }
  energia() { return this._energia }
  comer(gramos) { this._energia += gramos * 4 }
  volar(kms) { this._energia -= kms + 10 }
}
```

La clase `Golondrina` representa un modelo muy sencillo de un ave, en el que lo único que se registra es la energía que conserva. Se definen dos acciones: `comer` una cantidad de gramos de cierto alimento, lo que aumenta la energía de acuerdo al cálculo implementado en el método; y `volar` una cantidad de kilómetros, lo que disminuye la energía también de acuerdo al cálculo implementado.  
P.ej. si una golondrina come 30 gramos su energía aumenta en 120 unidades, mientras que si vuela 30 kilómetros su energía disminuye en 40 unidades.

Si en un entorno de prueba de JavaScript (ver los recursos [en la página inicial](./javascript-intro.md)) ingresamos este código, y luego definimos una golondrina y la hacemos comer 
```
const pepita = new Golondrina()
pepita.comer(30)
```
entonces la respuesta a 
```
pepita.energia()
```
será el número `120`.

Destacamos algunas particularidades de la definición de clases en JavaScript que se pueden apreciar en este ejemplo.

<br/>

## Los atributos no se definen, se usan directamente
JavaScript <span style="color: orange">**no**</span> requiere que los atributos de una clase se definan. Cada atributo se crea en el momento en que se evalúa una asignación. En nuestro ejemplo, el atributo `_energia` se genera al crear cada instancia de `Golondrina`, dado que se asigna en el constructor.

Recordemos (de [esta página](./javascript-arrays-strings-object-literals.md)) que las referencias a atributos inexistentes no generan un error sino que devuelven `undefined`. Lo mismo pasa con los atributos de una instancia. Si agregamos este método en la clase Golondrina
```
metodoQueFalla() { return this._atributoInexistente }
```
y probamos así
```
let pepi = new Golondrina()
pepi.metodoQueFalla()
```
no se va a generar un error, sino que vamos a obtener `undefined` como respuesta.

<br/>

## No se ponen modificadores de acceso ni indicador "esto es un método"
Revisemos la definición de este método
```
  energia() { return this._energia }
```
y comparémoslo con cómo podría ser en Java
```
  public int energia() { return _energia; }
```
en [Wollok](http://www.wollok.org/)
```
  method energia() { return _energia }
```
o en [Scala](https://docs.scala-lang.org/tour/classes.html)
```
  def energia() { return _energia }
```

En JavaScript no se pone ni modificador de acceso (el `public` de Java) ni una palabra que indique "esto es un método", como `method` en Wollok o `def` en Scala. Simplemente se pone el nombre del método, paréntesis, y la implementación entre llaves. Lo más conciso posible.  
En rigor, tampoco se pone el `int` que sí va en Java ... de eso hablamos en la siguiente sección.

<br/>

## Todo es público en JavaScript
<span style="color: dodgerblue">**Todos**</span> los atributos y métodos de una clase JavaScript son <span style="color: dodgerblue">**públicos**</span>, y no hay ninguna forma (al menos sencila) de evitarlo. Si siguiendo a la definición de `pepita` indicada más arriba ponemos
```
pepita._energia
```
vamos a obtener un bonito `120` como respuesta. 

Lo que *se puede* hacer, y vamos a proponer en el curso, es tener *la disciplina* de no usar atributos desde fuera de la definición de una clase. 
Para reforzar esto, recomendamos seguir una **convención**: que los nombres de atributo empiecen con un guión bajo, como `_energia` en el ejemplo.

Esta convención también va a ayudar a que no se "pisen" entre ellos los nombres de atributo y de método. En JavaScript, una clase no puede tener un atributo y un método con el mismo nombre, va a tomar como válido solamente uno de los dos. Si definimos
```
class Golondrina {
  constructor() { this.energia = 0 }
  energia() { return this.energia }
  comer(gramos) { this.energia += gramos * 4 }
  volar(kms) { this.energia -= kms + 10 }
}
```
el atributo `energia` va a estar definido, pero el método `energia()` no.

<br/>

## No se ponen los tipos de nada
Comparemos ahora este método
```
  comer(gramos) { this._energia += gramos * 4 }
```
con el análogo en Java
```
  public void comer(int gramos) { this._energia += gramos * 4; }
```

En JavaScript no se pone ni el tipo de retorno (`void` en este ejemplo, `int` en `energia()` que vimos antes), ni el tipo de los parámetros (`int` para el parámetro del método `comer`). 
Esto está relacionado con el hecho que JavaScript no hace chequeos de tipo antes de ejecutar.

El que le interese un primito de JavaScript que sí incorpora chequeos de tipo, puede mirar [TypeScript](http://www.typescriptlang.org/).

<br/>

## Es necesario poner `this.` para acceder a los atributos
Eso, ni más ni menos. En Java el método `comer` también puede definirse así
```
  public void comer(int gramos) { _energia += gramos * 4 }
```
sin poner `this.` en la referencia al atributo. En JavaScript esto no anda, una definición así
```
  comer(gramos) { _energia += gramos * 4 }
```
genera el error `_energia is not defined` al querer usar el método.

<br/>

## El punto-y-coma al final de cada sentencia es optativo
Eso, ver que el código de los métodos en Java requiere un punto-y-coma al final. En JavaScript este punto-y-coma es optativo (mientras se ponga una sentencia por línea), se puede poner o no.

Esto vale también para los métodos de más de una línea, p.ej. esta definición de método para agregar a la clase `Golondrina` es correcta
```
  darVueltaHabitual() {
    this.volar(20)
    this.comer(100)
    this.volar(20) 
  }
```

También se puede hacer poniendo los punto-y-coma
```
  darVueltaHabitual() {
    this.volar(20);
    this.comer(100);
    this.volar(20);
  }
```

Alguuuna vez podría ser necesario poner un punto-y-coma para que JavaScript entienda el código, pero es muy raro (al menos al momento de escribir esto, en marzo de 2018).

Sí es obligatorio el punto-y-coma si se ponen varias sentencias en la misma línea, p.ej. si se define `darVueltaHabitual` así
```
  darVueltaHabitual() {
    this.volar(20); this.comer(100); this.volar(20)
  }
```
estos punto-y-coma no se pueden obviar.
