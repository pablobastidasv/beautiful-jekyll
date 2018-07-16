--
layout: post
published: true
title: 'React-TS (3): Adicionando Propiedades a un componente '
---

Continuando con esta introducción a React usando TypeScript, ahora vamos a hacer que el componente del [post anterior]({{site.baseurl}}/2018-07-02-primer-componente-en-react/) reciba información desde el componente que lo llama. Esto nos permitirá reutilizar el componente varias veces.

**Entorno**:

  - MacOS High Sierra `Version 10.13.4`
  - Visual studio code `Version 1.24.1`
  - Node `v8.11.1`
  - npm `Version 6.1.0`
  - iTerm2 `Build 3.1.6`

## Agregar propiedades al componente

Vamos a empezar agregando las propiedades al componente. Al TypeScript ser un lenguaje tipado, debemos tener en cuenta que debemos declarar las propiedades del componente.

Para esto seguiremos los siguientes pasos:

 - Agregar tipado al componente, esto se consigue agregando `<any, any>` en la clase extendida.
 - Crear el(los) atributo(s) a usar.
 - Crear un constructor donde inicializar los atributos.
 - Utilizar los atributos en el componente.

**Manos a la obra**

Abrimos el componente creado anteriormente (`mi_input.tsx`) y modificamos la linea de la declaración de la clase agregando `<any, any>` a `React.Component<any, any>`.

```Typescript
class MiInput extends React.Component<any, any> {
```

Agregamos atributos `label` y `value` al componente.

```Typescript
private label: string;
private value: string;
```

Creamos un constructor para nuestro componente, este recibirá un objeto de tipo `any` el cual llamaremos `props` e inicializaremos los atributos del paso anterior.

```Typescript
constructor(props: any) {
    super(props);
    this.label = props.label;
    this.value = props.value;
}
```

Ahora vamos a utilizar los atributos que acabos de crear e inicializar, dentro de nuestro componente.

```Typescript
<div className="input_group">
    <label>{this.label}</label>
    <input type="text" value={this.value} />
</div>
```

Aquí vemos que en el label pusimos `{this.label}` lo cual referencia el atributo label creado en la clase y en el input vemos otra diferencia con `React` y `Html`, en `React` no debemos poner las comillas dobles (") cuando el valor a asignar a un atributo es el de una variable `value={this.value}`.

**Tadaaaa...** ya tenemos un componente que recibe valores desde otros componentes, ahora vamos a nuestro componente principal y enviemos información hasta este nuevo componente.

## Usando los atributos del componente desde otro

Abramos el archivo `App.tsx`, anteriormente estábamos llamando nuestro `MiInput` desde aquí, pero ahora debemos enviarle unos valores, estos valores los enviaremos indicando el nombre del atributo y el valor a enviar. En este caso los atributos son `label` y `value`. Quedaría de la siguiente forma.

``` Typescript
<MiInput
  label="Primer nombre"
  value="James" />
```

Perooo... **Cuando definimos el nombre de los atributos???**

Al momento de crear el constructor, nosotros indicamos los nombres de los atributos que íbamos a revisar del objeto `props` que recibimos en el constructor, estos son los nombres que los atributos del componente van a tener (`props.label`,`props.value`).

**Enviando valores de variables al Componente**

Ya vimos que podemos enviar valores fijos a nuestro componente como lo hicimos con `label="Primer nombre"`, pero y si no queremos un valor fijo, y en lugar de esto queremos una variable, como se haría...?

Para esto creamos la variable que vamos a enviar en nuestro componente "padre" y le asignamos un valor

``` typescript
private primerNombre: string = "James";
```

Y ahora en el llamado del componente ponernos esta variable en el valor que lo queremos, en este caso, como valor del atributo `value`.

```typescript
value={this.primerNombre}
```

El resultado ahora de nuestro archivo `App.tsx` debería verse de la siguiente forma:

```TypeScript
import * as React from 'react';
import MiInput from './component/mi_input';

class App extends React.Component {

  private primerNombre: string = "James";

  public render() {
    return (
      <div>
        <MiInput
          label="Primer nombre"
          value={this.primerNombre} />
      </div>
    );
  }
}

export default App;
```

**Reutilizando el componente**

Ahora el componente `MiInput` es un componente reutilizable, vamos ahora a agregar los campos "Segundo nombre", "Primer apellido", "Segundo apellido" y "Número de documento" en el componente principal (`App.tsx`) utilizando el componente `MiInput` para cada uno de estos valores.

De la siguiente forma estaremos reutilizando el componentes `MiInput` varias veces dentro de un mismo componente (`App.tsx`).

``` TypeScript
  ...

  <div>

    ...

    <MiInput
      label="Primer nombre"
      value={this.primerNombre} />

    <MiInput
      label="Segundo nombre"
      value={this.segundoNombre} />

    ...

  </div>

  ...
```

**Cadenas de componentes**

Ya hemos utilizado el componente `MiInput` varias veces dentro del componente `App.tsx`, ahora vamos a crear un componente que nos va a mostrar toda la información de una persona y otro para ver toda la información de un contrato, estos componentes lo llamaremos `InfoPersona` e `InfoContrato` respectivamente.

La idea de esto es que el componente `App.tsx` nos quede de la siguiente forma.

```TypeScript
import * as React from 'react';
import InfoPersona from './component/info_persona';
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

... Esta solución la veremos en el siguiente Post.
