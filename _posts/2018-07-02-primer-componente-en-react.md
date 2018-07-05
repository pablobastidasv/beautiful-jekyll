---
layout: post
published: true
title: 'React-TS (2): Primer componente en React'
---

Una vez creado nuestro proyecto, ahora vamos a crear un primer componente en react.

**Entorno**:
  - MacOS High Sierra `Version 10.13.4`
  - Visual studio code `Version 1.24.1`
  - Node `v8.11.1`
  - npm `Version 6.1.0`
  - iTerm2 `Build 3.1.6`

## Primer componente

Empezaremos con un componente sencillo, como el que vemos a continuacion:

![avatar-icon.png]({{site.baseurl}}/img/first_component/small_component.png)

Revisandolo veremos que es un `input` con su respectivo `label`, es decir, este componente esta conformado por un label y un input.

## Manos a la obra

Antes de empezar debemos iniciar nuestro servidor de desarrollo (en caso que no este ya iniciado) ejecutando el comando `npm run start` en la `consola/terminal` desde la carpeta de nuestro proyecto.

Abrimos la carpeta donde tenemos ubicado nuestro proyecto con el editor de texto de su elección (nosotros usaremos Visual studio code).

Una vez abierto el proyecto crearemos una carpeta llamada `components` dentro de la carpeta `src` y a su vez dentro de esta crearemos un archivo que llamaremos `primer_componente.tsx`.

Teoria: Un componente en react es una `clase` que extiende de `React.Component`, esta clase tiene un metodo llamaro `public render()` dentro del cual ubicaremos el codigo a devolver en un formato que es muy similar al ya conocido `html` aunque este tiene algunas adiciones que ya proximamente iremos viendo.

Ahora en este archivo que acabamos de crear pondremos el siguiente contenido:

```
import * as React from 'react';

class PrimerComponente extends React.Component {
  public render() {
    return (
      <div>Hola Mundo!!!</div>
    );
  }
}

export default PrimerComponente;
```

Tada!!!! ya hemos creado nuestro primer componente.

## Como usar el componente (PrimerComponente)

Ya con el componente creado la pregunta ahora es como utilizarlo, para esto debemos entender que el componente se utiliza como si este fuera una etiqueta mas de `html` la cual podemos usar en cualquiera de nuestros archivos `tsx`.

El nombre de la etiqueta corresponde al nombre de la clase que la represente, en este caso el nombre de la etiqueta será `PrimerComponente`, ya que la clase se llama asi.

Y lo usamos de la siguiente forma `<PrimerComponente />`.

Para ver esto en funcionamiento vamos al archivo llamado `App.tsx` que esta dentro de la carpeta `src`, y usamos el componente dentro de él.

El archivo debe verse de la siguiente forma:

```
import * as React from 'react';
import PrimerComponente from './component/primer_componente';

class App extends React.Component {
  public render() {
    return (
      <div>
        <PrimerComponente />
      </div>
    );
  }
}

export default App;
```

Guardamos y vamos al navegador a ver el resultado, podremos ver en pantalla el mensaje "Hola mundo!!!" que habiamos puesto en nuestro componente.

## Completando el componente

Ya creamos el componente, pero aun no es lo que queremos, vamos ahora a crear el contenido que este componente debe tener, para esto agregaremos el siguiente `html` que necesitamos, en este caso un `div`, un `label` y un `input`.

```
<div>
    <label>Primer nombre</label>
    <input type="text" value="James" />
</div>
```

Ya tenemos los elementos del componente solo nos falta "embellecerlos" con `css`. Para esto creamos un archivo `css` con el nombre `primer_componente.css` dentro de la carpeta `src/component` con el siguiente contenido.

```
.input_group{
    font-family: Roboto;
    display:  flex;
    flex-direction:  column;
    margin-top: 20px;
    margin-right: 20px;
}

.input_group label {
    height: 14px;
    font-size: 12px;
    line-height: 1.17;
    color: rgba(0, 0, 0, 0.54);
}

.input_group input{
    font-size: 16px;
    line-height: 1.5;
    letter-spacing: normal;
    width: 269px;
    border: 0;
    border-bottom: solid 2px rgba(0, 0, 0, 0.54);
}
```

**Importando el `css`**: En React el import de un archivo `css` se realiza dentro del archivo `tsx` como un objeto normal con la sentencia `import` de la siguiente forma:

```
import "./primer_componente.css";
```

**Aplicando el estilo**: Como mensioné anteriormente, en el metodo `render()` de React se escribe un código muy similar al html pero es igual, una de las diferencias es que en `html` el atributo para aplicar una clase css a un elemento es el `class`, en React este atributo pasa a llamarse `className`.

Aplicamos el estilo `input_group` al elemento `div`, quedando de la siguiente forma:

```
<div className="input_group">
  <label >Primer nombre</label>
  <input type="text" value="James" />
</div>
```

Y listo, ya tenemos nuestro componente como esperamos verlo, guardamos todos los cambios, vamos a nuestro navegador y deberiamos poder ver nuestro componente siendo visualizado en la pantalla.
