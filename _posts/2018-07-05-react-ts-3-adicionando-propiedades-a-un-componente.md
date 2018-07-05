---
layout: post
published: true
title: 'React-TS (3): Adicionando Propiedades a un componente '
---

Continuando con esta introducción a React usando Typescript, ahora vamos a hacer que el componente del [post anterior]({{site.baseurl}}/2018-07-02-primer-componente-en-react.md) reciba informacion desde el componente que lo llama. Esto nos permitirá reutilizar el componente varias veces.

**Entorno**:

  - MacOS High Sierra `Version 10.13.4`
  - Visual studio code `Version 1.24.1`
  - Node `v8.11.1`
  - npm `Version 6.1.0`
  - iTerm2 `Build 3.1.6`

## Agregar propiedades al componente

Vamos a empezar agregando las propiedades al componente. Al Typescript ser un lenguaje tipado, debemos tener en cuenta que debemos declarar las propiedades del componente.

Para esto seguiremos los siguientes pasos:

 - Agregar tipado al componente, esto se consigue agregando `<any, any>` en la clase extendida.
 - Crear el(los) atributo(s) a usar.
 - Crear un constructor donde inicializar los atributos.
 - Utilizar los atributos en el componente.

**Manos a la obra**

Abrimos el componente creado anteriormente (`primer_componente.tsx`) y modificamos la linea de la declaracion de la clase agregando `<any, any>` a `React.Component<any, any>`.

```Typescript
class PrimerComponente extends React.Component<any, any> {
```

Agregamos atributos `label` y `value` al componente.

```Typescript
private label: string;
private value: string;
```

Creamos un constructor para nuestro componente, este recibira un objeto de tipo `any` el cual llamaremos `props` e inicializaremos los atributos del paso anterior.

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
    <label >{this.label}</label>
    <input type="text" value={this.value} />
</div>
```

Aqui vemos que en el label pusimos `{this.label}` lo cual referencia el atributo label creado en la clase y en el input vemos otra diferencia con `React` y `Html`, en `React` no debemos poner las commilas dobles (") cuando el valor a asignar a un atributo es el de una variable `value={this.value}`.

**Tadaaaa...** ya tenemos un componente que recibe valores desde otros componentes, ahora vamos a nuestro componente principal y enviemos información hasta este nuevo componente.

## Usando los atributos del componente desde otro

Abramos el archivo `App.tsx`, anteriormente estabamos llamando nuestro `PrimerComponente` desde aqui, pero ahora debemos enviarle unos valores, estos valores los enviaremos indicando el nombre del atributo y el valor a enviar. En este caso los atributos son `label` y `value`. Quedaria de la siguiente forma.

``` Typescript
<PrimerComponente
  label="Primer nombre"
  value="James" />
```

Perooo... **Cuando definimos el nombre de los atributos???**

Al momento de crear el constructor, nosotros indicamos los nombres de los atributos que ibamos a revisar del objeto `props` que recibimos en el constructor, estos son los nombres que los atributos del componente van a tener (`props.label`,`props.value`).

**Enviando valores de variables al Componente**

Ya vimos que podemos enviar valores fijos a nuestro componente como lo hicimos con `label="Primer nombre"`, pero y si no queremos un valor fijo, y en lugar de esto queremos una variable, como se haría...?

Para esto creamos la variable que vamos a enviar en nuestro componente "padre" y le asignamos un valor

``` typescript
private primerNombre: string = "James";
```

Y ahora en el llamado del componente ponermos esta variable en el valor que lo queremos, en este caso, como valor del atributo `value`.

```typescript
value={this.primerNombre}
```

**Reutilizando el componente**

Ahora tenemos un componente reutilizable, vamos ahora a agregar los campos de "Segundo nombre", "Primer apellido", "Segundo apellido" y "Número de documento", esto lo lograremos agregando el componente por cada uno de estos nuevos campos con el los valores que queramos... hmmmm... dejemos esto de tarea, la solución en el proximo Post.
