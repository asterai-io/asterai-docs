---
title: Environments
---

Environments are deployable bundles that combine components with configuration. They are the unit of deployment in asterai.

## What is an Environment?

An environment is a runtime context that:
- Contains one or more components
- Holds configuration (environment variables, secrets)
- Can run locally or in the cloud
- Provides isolation between deployments

Think of components as reusable building blocks, and environments as the assembled application that runs them.

## Creating an Environment

Create a new environment with the CLI:

```bash
asterai env init my-env
```

This creates an empty environment. Add components to it:

```bash
asterai env add my-env --component your-username:hello-world@0.1.0
asterai env add my-env --component other-user:useful-tool@1.2.0
```

## Configuration

Environments support configuration through environment variables.

### Setting Variables

```bash
asterai env set-var my-env --var API_KEY=sk-abc123
asterai env set-var my-env --var DEBUG=true
```

### Accessing Variables in Components

Components access environment variables through the asterai host API:

```ts
import * as asterai from "asterai:host/api@0.1.0";

const apiKey = asterai.getEnv("API_KEY");
```

### Secrets

For sensitive values like API keys, use the cloud console to set secrets. Secrets are encrypted at rest and only decrypted at runtime.

## Running Environments

### Locally

Run an environment on your machine for development and testing:

```bash
asterai env run my-env
```

This starts a local runtime that loads your components and configuration. You can then call functions:

```bash
asterai env call my-env your-username:hello-world greeting.get-greeting '"World"'
```

### In the Cloud

Push your environment to run it on asterai's infrastructure:

```bash
asterai env push my-env
```

Once pushed, your environment is available via the asterai API. No infrastructure management required.

## Composing Components

Environments can contain multiple components that work together. Each component can import and call functions from other components in the same environment.

Example: An environment with a web scraper component and a data processing component:

```bash
asterai env init data-pipeline
asterai env add data-pipeline --component your-username:web-scraper@1.0.0
asterai env add data-pipeline --component your-username:data-processor@1.0.0
```

The data processor can import and call functions from the web scraper, creating a pipeline.

## Inspecting Environments

View the details of an environment:

```bash
asterai env inspect my-env
```

This shows:
- Components included
- Configuration variables (values hidden for secrets)
- Version information

## Managing Environments

```bash
asterai env list                    # List all your environments
asterai env pull my-env             # Pull an environment from the registry
asterai env remove my-env --component your-username:hello-world@0.1.0  # Remove a component
```

## Next Steps

- [Hello World guide](/src/hello_world): Create your first component and environment
- [Components](/src/components): Learn how to build components
- [CLI reference](/src/console_and_cli): Full CLI command reference
