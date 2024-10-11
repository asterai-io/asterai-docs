# Plugins
*this section is a work in progress*

Plugins are the core feature of asterai.
A plugin is a WebAssembly module, which can be written in
[AssemblyScript][asc], a TypeScript-like language.

Plugins have access to a range of functionality such as LLMs and Vector DBs.
They can also make HTTP calls and establish and manage WebSocket connections.

Therefore, a plugin can act as an bridge that connects AI to
application logic.

## Plugin manifest
The plugin manifest is a [Protobuf][protobuf] (.proto) file written used to
expose functionality from your plugin to both an LLM and other plugins.

A plugin manifest for a burger ordering plugin could look something like this:

```protobuf
syntax = "proto3";

service BurgerShop {
  // Orders a burger to be delivered to a specific address.
  rpc orderBurger(Order) returns (OrderResult);
}

message Order {
  // The address to deliver the burger to.
  string address = 1;
}

message OrderResult {
  string system_message = 1;
}
```

The manifest file describes the name of your plugin through the `service`
keyword in protobuf, the exported plugin functions through the `rpc` keyword,
and message types exchanged as function inputs and outputs.

The manifest file also generates convenience types for your plugin for each
`message` declared in your plugin manifest.
To generate types from the protobuf manifest run `asterai codegen`
from your plugin's directory, which you can import from AssemblyScript code.

## Plugin module
The plugin module is the AssemblyScript file that handles requests.
This compiles to a WebAssembly with `asterai build` and can be deployed
to your app with `asterai deploy --app <your_app_id>`.

Following from the burger example above, the plugin module could look something
like this:

```ts
import { Log } from "@asterai/sdk";
import {Order} from "./generated/Order";
import {OrderResult} from "./generated/OrderResult";

export function orderBurger(order: Order): OrderResult {
  Log.info("a burger is being ordered!");
  // TODO: make http call to burger API.
  return new OrderResult(`burger delivered to ${order.address}`);
}
```

Notice how the function receives structured data and outputs structured data,
as defined by the types in the plugin manifest.
This allows for seamless interoperability between reliable code and LLMs.

[asc]: https://www.assemblyscript.org
[protobuf]: https://protobuf.dev/overview/
