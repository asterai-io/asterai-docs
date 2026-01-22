Components are the building blocks of asterai. A component is a portable, sandboxed program that can be published to the registry and run anywhere.

## What is a Component?

A component is compiled code with a typed interface. You write it in a supported language (TypeScript, Python, Rust, Go, etc.), define its interface, and asterai compiles it to a portable format that runs in any asterai environment.

Components can:
- Export functions for other components or AI agents to call
- Import and use other components
- Access asterai's built-in capabilities (HTTP, storage, LLM calls)

## Component Interface

Every component has an interface defined in [WIT (WebAssembly Interface Types)](https://component-model.bytecodealliance.org/design/wit.html). This defines what functions your component exports and what types it uses.

Example interface for a burger ordering tool:

```wit
package your-username:burger-shop@0.1.0;

world component {
  import asterai:host/api@0.1.0;

  export order-burger: func(order: order) -> order-result;

  record order {
    address: string,
  }

  record order-result {
    error: option<string>,
  }
}
```

The interface declares:
- **Package**: Your namespace, component name, and version
- **Imports**: Capabilities your component needs (here, the asterai host API)
- **Exports**: Functions your component provides
- **Types**: Data structures used by your functions

## Component Implementation

The implementation is your actual code. Here's the TypeScript implementation for the interface above:

```ts
import * as asterai from "asterai:host/api@0.1.0";
import { Order, OrderResult } from "your-username:burger-shop/component@0.1.0";

export const orderBurger = (order: Order): OrderResult => {
  console.log(`Burger order for: ${order.address}`);
  asterai.sendResponse(`Burger delivered to "${order.address}"`);
  return { error: undefined };
};
```

The same component in Rust:

```rust
use asterai_host::api as asterai;

#[derive(Debug)]
pub struct Order {
    pub address: String,
}

#[derive(Debug)]
pub struct OrderResult {
    pub error: Option<String>,
}

pub fn order_burger(order: Order) -> OrderResult {
    println!("Burger order for: {}", order.address);
    asterai::send_response(&format!("Burger delivered to \"{}\"", order.address));
    OrderResult { error: None }
}
```

## Versioning

Components use semantic versioning. Each published version is immutable—you can't overwrite an existing version. This ensures reproducible builds and reliable dependencies.

## Next Steps

- [Hello World guide](/src/hello_world): Create and deploy your first component
- [CLI reference](/src/console_and_cli): Learn the asterai CLI commands
- [Registry](/src/registry): Publish and discover components
