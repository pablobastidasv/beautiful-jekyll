---
layout: post
published: true
title: 'React-TS (1): React y typescript - Hola mundo'
---

Este post explica como crear un *"Hola mundo"* utilizando [React](https://reactjs.org/) con [TypeScript](https://www.typescriptlang.org/), no se enfocara en detallar paso a paso o que significa cada comando o configuración realizada, únicamente que hacer para que funcione.

**Entorno**:
  - MacOS High Sierra `Version 10.13.4`
  - Visual studio code `Version 1.24.1`
  - Node `v8.11.1`
  - npm `Version 6.1.0`
  - iTerm2 `Build 3.1.6`

## Antes de empezar

  1. Instalar TypeScript

Con el siguiente comando se instala TypeScript:

```bash
npm install -g typescript
```

Para verificar que la instalación se efectuó correctamente

```bash
tsc -v
```

Esta instrucción muestra la versión instalada, en el momento de realizar este post la ultima versión es `Version 2.9.2`

  2. Instalar `create-react-app`

```
npm install -g create-react-app
```

## Manos a la obra

**Crear el proyecto**:

```bash
create-react-app my-app --scripts-version=react-scripts-ts
```

**Ejecutar el proyecto**:

Ingresa a la carpeta de la aplicación, en este ejemplo se llama `my-app`.

```
cd my-app
```

Ahora usamos `npm` para ejecutar el proyecto.

```
npm run start
```

Esto abrirá una ventana del navegador con la aplicación recién creada.

## Referencia

[TypeScript React Starter](https://github.com/Microsoft/TypeScript-React-Starter)
