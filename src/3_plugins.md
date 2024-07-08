# Plugins
*this section is a work in progress*

Plugins are the core feature of asterai.
A plugin is a WebAssembly module, which can be written in
[AssemblyScript][asc], a TypeScript-like language.

Plugins have access to a range of functionality such as LLMs and Vector DBs.
They can also make HTTP calls and establish and manage WebSocket connections.

Therefore, a plugin can act as an integral bridge, connecting AI to
applications.

## Plugin manifest
The plugin manifest is a file written in YAML used to described to AI what your
plugin does.
It is also used to generate convenience argument types, via `asterai codegen`,
that you can import from AssemblyScript code.

A plugin manifest for a burger ordering plugin could look something like this:

```yaml
name: plugin
functions:
  - name: orderBurger
    description: >-
      orders a burger to be delivered to the specified address
    arguments:
      - name: address
        type: string
        description: the address to deliver the burger to
```

## Plugin module
The plugin module is the AssemblyScript file that handles requests.
This compiles to a WebAssembly with `asterai build` and can be deployed
to your app with `asterai deploy --app <your_app_id>`.

Following from the burger example, the plugin module could look something like
this:

```ts
import { OrderBurgerArgs } from "./generated/OrderBurgerArgs";
export * from "@asterai-io/sdk/exports";

export function orderBurger(args: OrderBurgerArgs): string {
  // TODO: make http call to burger API.
  return `burger delivered to ${args.address}`;
}
```

[asc]: https://www.assemblyscript.org
