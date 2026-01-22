**You don't need to know WebAssembly to use asterai.** Write components in TypeScript, Python, Rust, Go, or any supported language. The asterai CLI handles compilation automatically.

This page is for those curious about the underlying technology.

## Why WebAssembly?

Asterai uses WebAssembly (WASM) as its portable execution format. This gives us:

- **Language independence**: Any language that compiles to WASM works with asterai
- **Sandboxed execution**: Components run in isolation with explicit permissions
- **Near-native performance**: WASM executes efficiently on any platform
- **Portability**: The same compiled component runs locally, in the cloud, or at the edge

## WASI and the Component Model

Asterai uses [WASI (WebAssembly System Interface)](https://wasi.dev/) Preview 2 and the [WebAssembly Component Model](https://component-model.bytecodealliance.org/). This is an emerging standard for building modular, composable WebAssembly applications.

Key concepts:

- **Components**: Self-contained units with typed interfaces (not just raw WASM modules)
- **WIT (WebAssembly Interface Types)**: A language for defining component interfaces
- **Composition**: Components can import and export functionality, enabling true modularity

The Component Model solves a fundamental problem: how do you call a function written in Rust from TypeScript, or vice versa? WIT provides a common type system that works across all languages.

## Experimental Technology

The WebAssembly Component Model is still evolving. Asterai is making a bet on this technology as the future of modular, portable software.

What this means for you:

- **Tooling is improving rapidly**: Expect better error messages and faster compilation over time
- **Some rough edges**: You may encounter edge cases or limitations
- **Breaking changes possible**: The underlying standards are stabilizing but not frozen

We believe the benefits—true language interoperability, sandboxed execution, and universal portability—are worth the early-adopter tradeoffs.

## Learn More

For a deep dive into the Component Model and WIT:

- [Component Model documentation](https://component-model.bytecodealliance.org/)
- [WIT specification](https://component-model.bytecodealliance.org/design/wit.html)
- [WASI Preview 2](https://github.com/WebAssembly/WASI/blob/main/preview2/README.md)

The Bytecode Alliance documentation is the authoritative source for understanding these technologies.
