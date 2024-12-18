# Hello World
*this section is a work in progress*

This step-by-step guide describes how to create a new asterai application
that simply exposes a hardcoded name to the LLM via a plugin.
When you ask the LLM who to give hello to, it will have access to the name
within the plugin.

Think of this like sending a message to a pre-defined person in a contacts list.
Except, in this example plugin the actual HTTP request for sending the DM is
not sent.

1. Sign into the [asterai console](https://asterai.io/dashboard)
2. Create a new application
3. Install the asterai CLI:
```bash
npm install -g @asterai/cli 
```
4. Generate a new API key in asterai, and authenticate with it into the CLI:
```bash
asterai auth <your_api_key> 
```
5. Initialise a new project called `hello-world`:
```bash
asterai init hello-world 
```
6. Install dependencies on the new project:
```bash
cd hello-world
npm i 
```
7. Inspect the contents of `plugin.asterai.proto`, the plugin manifest file
8. Inspect the contents of `plugin.ts`, the plugin file
9. Modify the contents of `plugin.asterai.proto` so that it has a function
called `sayHello` instead of `orderBurger`.
10. Modify the function comment to "say hello to a pre-defined person".
11. This function call does not require any arguments, therefore update the
input and output types to `Empty`, defined as `message Empty {}`.
12. Run `asterai codegen`. Here, this has no effect because there are no
arguments (they are empty), but it is good practice to always run codegen
after modifying the manifest file to ensure the types are up to date.
13. Modify the `plugin.ts` file to have the new function name, `sayHello`.
14. Modify the return statement to return `"said hello to Alice"`
15. Get your app ID from the cloud console
16. Deploy the plugin:
```bash
asterai deploy --app <your_app_id>
```
17. Refresh the page in the cloud console.
Now you should see the new, active plugin that was just deployed.
18. In the playground section, ask "who should I say hello to?".
The app should reply with "Alice".
19. You can also make a POST request to
https://api.asterai.io/app/:your_app_id/query with a raw text body
containing the user query.
The response will be an [SSE][sse] of token streams.

Hopefully this hello world example illustrates how asterai can be used to
connect AI to applications.
Within plugins, it is possible to access LLMs, Vector DBs, make HTTP calls
and even use WebSockets.

[sse]: https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events
