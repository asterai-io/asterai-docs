# Plugins
Plugins are the core feature of Asterai agents.
It allows agents to interact with external resources through functions,
also known as tools.

Plugins can expose functionality such as interacting with HTTP APIs, knowledge
bases, databases and also other plugins.

A plugin is a program that is compiled into a WebAssembly module and deployed
into your agent.

Plugins can be written in any language that can be compiled to WebAssembly,
such as TypeScript, Python, Go, Rust, and many others.

Plugins can be as simple or complex as required for your agent.
Asterai offers a range of pre-existing tools to make common use cases extremely
simple to implement, such as having your agent answer questions from a
knowledge base.

## Plugin Interface
The Plugin Interface defines what functions your plugin has.
The interface file is in the [WIT][wit] file format. 

An example plugin interface file looks like this:

```wit
package your-asterai-username:burger-shop@0.1.0;

world plugin {
  import asterai:host/api@0.1.0;

  export order-burger: func(order: order) -> order-result;

  record order {
    // The address to deliver the burger to.
    address: string,
  }

  record order-result {
    error: option<string>,
  }
}
```

The first line defines the username of the owner of the plugin and the
name of the plugin. In this case, the plugin name is `burger-shop`.
It also defines a version, 0.1.0.
Plugins must have unique versions when deployed, so the same version
can't be deployed twice.

This example plugin has a single function, `order-burger`, which
takes in one argument, the `order` object, and returns another object,
`order-result`, which contains an optional `error` string.

The interface imports the `asterai:host` interface, which allows your
plugin to interact with asterai's SDK to do things such as sending
messages from the plugin to the agent.

## Plugin Module
The plugin module is the source code of the plugin, i.e. its implementation.
This can be written in any programming language that compiles to WebAssembly.

For example, the TypeScript implementation for the previous plugin interface
example could look something like this:

```ts
import * as asterai from "asterai:host/api@0.1.0";
import {
  Order,
  OrderResult
} from "your-asterai-username:burger-shop/plugin@0.1.0";

export const orderBurger = (order: Order): OrderResult => {
  // TODO: call order API.
  console.log(`burger order for address: ${order.address}`);
  // Tell agent about the outcome.
  asterai.sendResponseToAgent(`burger was delivered to "${order.address}"`);
  return {
    error: undefined
  } satisfies OrderResult;
};
```

For more information about how to build and deploy plugins,
look at [this guide][hello-world-guide].

[wit]: https://component-model.bytecodealliance.org/design/wit.html
[hello-world-guide]: https://docs.asterai.io/hello_world.html
