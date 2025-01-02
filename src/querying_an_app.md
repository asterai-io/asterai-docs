# Querying an asterai agent

## With the JavaScript & TypeScript client library
You can use our [TypeScript library][js-lib] to easily query an asterai
agent from a web client or web server with Node, Bun, Deno etc.
For a full interactive example in React, check out [yeet-the-cube][yeet].

### Examples
#### Query an agent and obtain a full text response back

```ts
import { AsteraiClient } from "@asterai/client";

const client = new AsteraiClient({
  appId: ASTERAI_APP_ID,
  queryKey: ASTERAI_PUBLIC_QUERY_KEY,
});

const response = await client.query({
  query: "how's the weather like in NY?"
});

console.log(await response.text());
```

#### Query an agent and obtain a response back token by token

```ts
import { AsteraiClient } from "@asterai/client";

const client = new AsteraiClient({
  appId: ASTERAI_APP_ID,
  queryKey: ASTERAI_PUBLIC_QUERY_KEY,
});

const response = await client.query({
  query: "how's the weather like in NY?"
});

let llmResponse = "";
response.onToken(token => {
  llmResponse += token;
});

response.onEnd(() => {
  // The full response has been received.
  console.log(llmResponse);
});
```


## With the HTTP API

To query an app, use the HTTP request below:

```http request
POST https://api.asterai.io/app/:app_id/query/:query_mode
```

### HTTP Response format

Currently the only supported query mode is `sse`, where the response
will be an [SSE][sse] of app response events.

Each SSE data event line will begin with one of these prefixes:

| SSE data event line prefix | Description                                    |
|----------------------------|------------------------------------------------|
| "llm-token: "              | An LLM response token                          |
| "plugin-output: "          | Plugin output message serialized with protobuf |

### Authorization

Note that you must set the `Authorization` header to an app query key.
Find our more about app query keys below.

## Query keys

To query your app, you need a query key.
You can generate a new public query key via the dashboard.

There are two types of keys: public keys and user keys.

### Public query key
When querying an app with a public key, there is no associated user data.

This is used for when you want everyone to have the same experience in your
app, or when the end user is not logged in.

> Note that "public" in this context simply means that there is no associated
user for the key.
Whether your app is open to the public is your choice.
If your app accesses internal or sensitive systems even without an user being
logged in, the "public query key" should not be leaked for security reasons.
This depends on the design of your app and plugins.

### User query keys
When querying an app with a user key, there is an associated user ID which
allows plugins to work with user-specific features, such as accessing
user key-value storage.

It is possible to generate a user query key using the following endpoint:

```http request
GET https://api.asterai.io/app/:app_id/query/key/user/:app_user_id

Response example:
{"key":"00000000-0000-0000-0000-000000000000"}
```

Where `:app_id` is your app's ID and `:app_user_id` is the ID of your app's
user, as a unique string (maximum of 64 characters).

Note that this is an authenticated request, so you must set the `Authorization`
header to your API key which can be found in your account page in the dashboard.

Once you have the user query key, you can query your app with the user key
by setting the `Authorization` header in the regular app query endpoint
(`POST /app/:app_id/query`).

## Client libraries for other languages

If you'd like to show your interest in a client library for a specific
programming language, join us on [Discord][discord] and let us know!

[sse]: https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events
[discord]: https://discord.gg/NRWrNmxR4E
[js-lib]: https://www.npmjs.com/package/@asterai/client
[yeet]: https://github.com/rellfy/yeet-the-cube
