Asterai is the tool marketplace for AI agents. Discover, share, and deploy tools written in any programming language, with instant cloud execution.

## What is asterai?

Asterai is a registry and runtime for portable, sandboxed tools. Write a tool once in your preferred language, publish it to the registry, and run it anywhere—locally or in the cloud.

Under the hood, asterai uses [WebAssembly](/src/webassembly) for portability and security. But you don't need to know anything about WebAssembly to use asterai. Just write code in a supported language (TypeScript, Python, Rust, Go, and more), and asterai handles the rest.

## Key Concepts

1. **Component**: A portable tool or library. Components are published to the registry and can be composed together. Write them in any supported language.

2. **Environment**: A deployable bundle of one or more components with configuration (environment variables, secrets). Environments can run locally or in the cloud.

3. **Registry**: Where components are published and discovered. Each user has a namespace for their components.

4. **CLI**: The open-source command-line tool for building, publishing, and running components locally.

5. **Cloud**: Run environments on asterai's infrastructure with a simple API call—no DevOps required.

## Why asterai?

**Language interoperability**
Write tools in any language. Components written in different languages work together seamlessly through typed interfaces.

**Sandboxed execution**
AI agents can run untrusted code safely. Each component runs in an isolated sandbox with explicit permissions.

**True portability**
Deploy anywhere. No dependency hell. Same behavior locally and in the cloud.

**Instant deployment**
Tools just work. No containers, no infrastructure configuration. Publish and run.

## Example Use Cases

### Tools for AI Agents
Build reliable tools that your AI agents can call: API integrations, data processing, web scraping, file operations. Components provide type-safe interfaces that LLMs can understand and use correctly.

### Polyglot Libraries
Use the right language for each job. A Rust component for performance-critical math, a Python component for ML inference, a TypeScript component for API calls—all composable in a single environment.

### Serverless Functions
Deploy functions to the cloud without managing infrastructure. Pay only for what you use, with global edge execution for low latency.

## Getting Started

The fastest way to get started is the [Hello World guide](/src/hello_world), which walks you through creating and deploying your first component.
