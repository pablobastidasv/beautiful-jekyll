---
layout: post
published: truxe
title: 'React-TS (4): Componentes sin estado (Stateless)'
---
Que es estado? Se habla de estado cuando se mantiene información. Hasta el momento hemos 
creando componentes que manejan estado, esto hace que componentes que deberían
ser sencillos como simples mensajes personalizados, adquieran una complejidad innecesaria. A continuación vamos a
revisar como lograr que un componente que no requiere estado, no lo tenga.

**Entorno**:
  - MacOS High Sierra `Version 10.13.4`
  - Visual studio code `Version 1.24.1`
  - Node `v8.11.1`
  - npm `Version 6.1.0`
  - iTerm2 `Build 3.1.6`

## Componente con estado (Stateful)

En React, los componentes creados con una clase extendiendo de `React.Component` son componentes que manejan estado, ya que al
crear una instancia, se esta creando una instancia de un objeto la cual puede almacenar propiedades en ella, estas propiedad pueden
almacenar información durante el tiempo de vida de la instancia, esto se denomina mantener estado.

A continuación veremos un componente cuya única función es mostrarnos en pantalla un mensaje, el cual dice "Hello TypeScript!"
donde el "Hello" esta quemado en el componente, al "TypeScript" es recibido como atributo del objeto y el signo de admiración (!) 
se imprimirá según otro atributo, el cual demostrara el nivel de entusiasmo (`enthusiasmLevel`) imprimiendo un signo de exclamación
según el valor que tiene este atributo, para esto, este atributo sera un atributo de tipo numérico (`number`). 
 
**Codigo componente con estado**
```typescript
import * as React from 'react';
import './hello.css';

class Hello extends React.Component<any, any> {

    private name = "";
    private enthusiasmLevel = 1;

    constructor(props: any) {
        super(props);
        this.name = props.name;
        this.enthusiasmLevel = props.enthusiasmLevel;
    }

    public render() {
        return (
            <div className="hello"> <div className="greeting"> Hello {this.name + this.getExclamationMarks()}
                </div>
            </div> 
        );
    }

    private getExclamationMarks() {
        return Array(this.enthusiasmLevel + 1).join('!');
    }
}

export default Hello;
```

En este código vemos toda la complejidad que ha sido añadida a este componente, el cual ahora maneja estado, es una clase, etc. para
que al final su única función sea imprimir un mensaje. Al parecer este componente realmente no necesita todo este tipo de complejidad.

## Componente sin estado (Stateless)

Un componente sin estado en React se crea a partir de una función (`function`), esto nos da un nivel de complejidad mucho menor, ya que
no se trata de una clase, extender, sobreescribir, manejar constructor, estado, etc, solamente se trata de una función, que recibe un
atributo y retorna el "HTML" que necesita ser renderizado.

A continuación veamos un ejemplo, en el cual estamos tomando el mismo código del componente anterior y lo estamos migrando a un modelo 
sin estado (`stateless`): 

**Codigo componente sin estado**

```typescript
import * as React from 'react';
import './hello.css';

function Hello(props: any) {
    if (props.enthusiasmLevel <= 0) {
        throw new Error('You could be a little more enthusiastic. :D');
    }

    return (
        <div className="hello">
            <div className="greeting">
                Hello {props.name + getExclamationMarks(enthusiasmLevel)}
            </div>
        </div>
    );
}

function getExclamationMarks(numChars: number) {
    return Array(numChars + 1).join('!');
}

export default Hello;
```

En este código vemos como toda la complejidad que teníamos antes, se ve reducida a un solo método que retorna el "HTML" que sera renderizado
en el navegador, también se han adicionado un método y una validación para demostrar como interactuar en caso de componentes un poco mas
complejos, como en este caso, tenemos una función que mostrara el entusiasmo recibiendo el numero de caracteres que va a mostrar.

## Migrando un componente

En el post anterior se mostró un componente muy sencillo el cual llamamos `MiInput`, dicho componente solamente renderiza un label y un input
a partir de dos atributos que se le ingresan... Pero como ya lo hemos hecho antes, esta actividad la dejaremos para el próximo post y si creen
que ya aprendieron a crear componentes sin estado a partir de uno con estado, los invitamos a realizar esta conversión con el componente `MiInput`

