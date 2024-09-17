# Querying an asterai app

To query an app, use the HTTP request below:

```http request
POST https://api.asterai.io/app/:app_id/query
```

Note that you must set the `Authorization` header to an app query key.
Find our more about app query keys below.

The response will be an [SSE][sse] of token streams.

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
```

Where `:app_id` is your app's ID and `:app_user_id` is the ID of your app's
user, as a unique string (maximum of 64 characters).

Note that this is an authenticated request, so you must set the `Authorization`
header to your API key which can be found in your account page in the dashboard.

[sse]: https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events

Once you have the user query key, you can query your app with the user key
by setting the `Authorization` header in the regular app query endpoint
(`POST /app/:app_id/query`).
