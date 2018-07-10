---
layout: post
published: true
title: 'React-TS (3-1): Reutilizando el componente '
---
Ahora vamos a resolver el "ejercicio" que dejamos en el [post anterior](https://pablobastidasv.github.io/2018-07-05-react-ts-3-adicionando-propiedades-a-un-componente/) en el cual requeririamos reutilizacion de componentes de una manera mas retadora.

**Entorno**:

  - MacOS High Sierra `Version 10.13.4`
  - Visual studio code `Version 1.24.1`
  - Node `v8.11.1`
  - npm `Version 6.1.0`
  - iTerm2 `Build 3.1.6`

## Solucion

El ejercicio resuelto correspondria en 2 nuevos componentes `InfoPersona` e `InfoContrato` los cuales se verian de la siguiente manera:

** info_persona.tsx **

```typescript
import * as React from 'react';
import MiInput from './mi_input';
import './person.css';

class InfoPersona extends React.Component {
  private nombre: string = "";
  private apellido: string = "";
  private edad: string = "";

  public render() {
    return (
        <div>
            < 
                label="Nombre(s)" 
                value={this.nombre} />
            <MiInput 
                label="Apellido(s)" 
                value={this.apellido} />
            <MiInput 
                label="Edad" 
                value={this.edad} />
        </div>
    );
  }
}

export default InfoPersona;
```

** info_contrato.tsx **

```typescript
import * as React from 'react';
import MiInput from './mi_input';
import './person.css';

class InfoPersona extends React.Component {
  private tipo: string = "";
  private fechaInicio: string = "";
  private salario: string = "";

  public render() {
    return (
        <div>
            <MiInput 
                label="Tipo" 
                value={this.tipo} />
            <MiInput 
                label="Fecha de inicio" 
                value={this.fechaInicio} />
            <MiInput 
                label="Salario" 
                value={this.salario} />
        </div>
    );
  }
}

export default InfoPersona;
```

Con estos componentes ya creados estamos viendo como se reutiliza el componente creado en el primer capitulo (MiInput) en otros dos componentes y estos 2 nuevos componentes los podemos utilizar en otro componente, como nuestro `App.tsx`, quedando este de la siguiente forma.

```Typescript
import * as React from 'react';
import InfoPersona from './component/info_contrato';
import InfoContrato from './component/info_contrato';

class App extends React.Component {

  public render() {
    return (
      <div>
        <InfoPersona />
        <InfoContrato />
      </div>
    );
  }
}

export default App;
```
