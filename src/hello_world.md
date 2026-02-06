---
title: 🚀 Hello World
---

This guide walks you through creating your first asterai component and
running it in an environment.

## 📋 Prerequisites

- Node.js 18+
- An [asterai account](https://asterai.io)

## Overview

You'll create a simple component that exports a greeting function, then
run it locally in an environment.

## Steps

### 1. Install the CLI

```bash
npm install -g @asterai/cli
```

### 2. Authenticate

Generate an API key from
[the console](https://asterai.io/login):

```bash
asterai auth login <your_api_key>
```

Verify you're logged in:

```bash
asterai auth status
```

### 3. Create a new component

```bash
asterai component init hello-world
cd hello-world
```

This scaffolds a TypeScript component project with the following
structure:

```
hello-world/
  component.ts       # Component implementation
  component.wit      # WIT interface definition
  package.json       # Build scripts and dependencies
  tsconfig.json
  .gitignore
```

### 4. Understanding the interface

The scaffolded `component.wit` defines a simple interface. If you're
logged in, the CLI automatically sets your username as the namespace:

```wit
package your-username:hello-world@0.1.0;

interface hello-world {
  greet: func(name: string);
}

world component {
  import asterai:host/api@1.0.0;

  export hello-world;
}
```

This declares a component that exports one function: `greet`, which
takes a name and prints a greeting.

### 5. Understanding the implementation

The scaffolded `component.ts` implements the interface:

```ts
import * as host from "asterai:host/api@1.0.0";

const greet = (name: string) => {
  console.log(`hello ${name}!`);
};

export const helloWorld = {
  greet
};
```

The exported object name matches the interface name in `component.wit`
(kebab-case `hello-world` becomes camelCase `helloWorld` in TypeScript).

### 6. Install dependencies and build

```bash
npm install
asterai component build
```

### 7. Push the component

Push your component to the registry:

```bash
asterai component push
```

### 8. Create an environment

Create a new environment and add your component to it:

```bash
asterai env init my-env
asterai env add-component my-env your-username:hello-world@0.1.0
```

### 9. Call your function

Call your component's function:

```bash
asterai env call my-env your-username:hello-world hello-world.greet '"World"'
```

You should see: `hello World!` 🎉

### 10. Push to the cloud (optional)

To run your environment in the cloud, push it to the registry:

```bash
asterai env push my-env
```

Your environment is now available to run on asterai's cloud
infrastructure.

## 🎯 What's Next?

You've created a component and run it in an environment.
From here you can:

- ➕ Add more functions to your component
- 📥 Import other components from the registry
- 🔧 Add configuration (environment variables, secrets) to your
  environment
- 🔗 Compose multiple components in a single environment

See the [Components](/components) page for more on building components,
or [Registry](/registry) for publishing and discovering components.
