This guide walks you through creating your first asterai component and running it in an environment.

## Prerequisites

- Node.js 18+
- An [asterai account](https://asterai.io)

## Overview

You'll create a simple component that returns a greeting, then run it locally in an environment.

## Steps

### 1. Install the CLI

```bash
npm install -g @asterai/cli
```

### 2. Authenticate

Generate an API key from [your dashboard](https://asterai.io/dashboard/account):

```bash
asterai auth login <your_api_key>
```

Verify you're logged in:

```bash
asterai auth status
```

### 3. Create a new component

```bash
asterai component init hello-world typescript
cd hello-world
npm install
```

### 4. Define the interface

Edit `plugin.wit` to define your component's interface. Replace `your-username` with your asterai username:

```wit
package your-username:hello-world@0.1.0;

interface greeting {
  get-greeting: func(name: string) -> string;
}

world component {
  export greeting;
}
```

This declares a component that exports one function: `get-greeting`, which takes a name and returns a greeting string.

### 5. Implement the component

Edit `src/index.ts`:

```ts
import { Greeting } from "./bindings/interfaces/your-username-hello-world-greeting";

export const greeting: typeof Greeting = {
  getGreeting(name: string): string {
    return `Hello, ${name}!`;
  },
};
```

### 6. Build

```bash
npm run build
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
asterai env add my-env --component your-username:hello-world@0.1.0
```

### 9. Run locally

Run the environment locally:

```bash
asterai env run my-env
```

### 10. Call your function

In another terminal, call your component's function:

```bash
asterai env call my-env your-username:hello-world greeting.get-greeting '"World"'
```

You should see: `Hello, World!`

### 11. Push to the cloud (optional)

To run your environment in the cloud, push it to the registry:

```bash
asterai env push my-env
```

Your environment is now available to run on asterai's cloud infrastructure.

## What's Next?

You've created a component and run it in an environment. From here you can:

- Add more functions to your component
- Import other components from the registry
- Add configuration (environment variables, secrets) to your environment
- Compose multiple components in a single environment

See the [Components](/src/components) page for more on building components, or [Registry](/src/registry) for publishing and discovering components.
