# Más sobre clases en JavaScript

volver a [JavaScript](./javascript-intro.md)

<br/>

En la [página anterior](./javascript-clases-1.md) se contaron las características básicas de la definición de clases en JavaScript.

En esta, vamos a tratar algunas cuestiones que conviene manejar para definir lindos modelos de objetos usando JavaScript.

<br/>

## Herencia en JavaScript
Es muy parecido a Java. Creo que alcanza con mostrar este ejemplo, en donde se definene dos subclases de `Golondrina`.

```
class GolondrinaPensativa extends Golondrina {
  constructor() {
    super()
    this._nivelDeConcentracion = 10
  }
  pensar(minutos) { this._nivelDeConcentracion += minutos }
  comer(gramos) { 
    super.comer(gramos)
    this._nivelDeConcentracion -= 1
  }
  nivelDeConcentracion() { return this._nivelDeConcentracion }
}
   
class GolondrinaGolosa extends Golondrina {
  constructor() {
    super()
    this._loUltimoQueHizoFueComerMucho = false
  }
  comer(gramos) { 
    super.comer(gramos)
    if (gramos > 50) { 
      this._loUltimoQueHizoFueComerMucho = true
    }
  }
  estaFeliz() { return this._loUltimoQueHizoFueComerMucho }
}
```

Una `GolondrinaPensativa` define una nueva acción que es `pensar`, y mantiene un nivel de concentración. Una `GolondrinaGolosa` está feliz si lo último que hizo fue comer mucho.

Notar que
- se usa `extends` como en Java
- en una subclase se pueden definir nuevos atributos
- en una subclase se pueden definir métodos que no tiene la superclase, p.ej. `nivelDeConcentracion()` en `GolondrinaPensativa`.
- en una subclase se puede redefinir un método heredado, en este caso `comer(gramos)` en ambas subclases, y acceder a la implementación de la superclase poniendo `super`.


## Consecuencias de la falta de chequeo de tipos
Ya vimos que al no haber chequeo de tipos antes de la ejecución, en JavaScript no se ponen, al definir un método, ni el tipo de retorno ni los tipos de los parámetros. Tampoco se definen los tipos de los atributos.

Esta no es la única consecuencia de no tener chequeos de tipo en JavaScript. Veamos otras.

<br/>

### El polimorfismo no está limitado por los tipos
El polimorfismo no está limitado por jerarquías de clases o cuestiones de tipos. La única condición que tienen dos objetos (que incluso pueden ser o no instancias de clases, recordar lo que se cuenta [en esta página](./javascript-arrays-strings-object-literals)) para ser polimórficos para un tercero, es que entiendan los mensajes que el tercero les envía.

Si definimos estas tres clases (repetimos la versión original de `Golondrina` para que el ejemplo sea más fácil de ver)
```
class Golondrina {
  constructor() { this._energia = 0 }
  energia() { return this._energia }
  comer(gramos) { this._energia += gramos * 4 }
  volar(kms) { this._energia -= kms + 10 }
}

class TamagotchiVolador {
  constructor() { this._felicidad = 300; this._edad = 0 }
  comer(gramos) { this._felicidad += 5; this._edad += 1 }
  volar(kms) { this._felicidad += kms; this._edad += 1 }
  llorar(minutos) { 
    this._felicidad -= 10 * minutos
    this._edad += minutos
  }
}

class Entrenador {
  entrenar(cosa) { 
    cosa.volar(20) ; cosa.comer(100) ; cosa.volar(20)
  }
}
```

y estos objetos
```
const pepita = new Golondrina()
pepita.comer(30)
const tomi = new TamagotchiVolador()
const roque = new Entrenador()
```

entonces podemos hacer `roque.entrenar(pepita)` y también `roque.entrenar(tomi)`.

<br/>

### No es necesario poner los métodos abstractos
