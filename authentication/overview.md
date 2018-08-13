# Authentication

*Any user may create one client that only they can authorize (for all intents and purposes, only they can use it).*

pnut.io implements parts of the [OAuth 2.0 standard](https://oauth.net/2/) to secure access between clients, users, and the API.

To authenticate and retrieve an app token or a token on behalf of a user, you will need to have an active client.

Once you have created a client from the [Develop frontpage](https://pnut.io/dev), read through the implementation details and choose what [Scopes](../authentication/scope) you will need to authorize, and an appropriate Flow to authorize them with:

* [Web Flows](../authentication/web-flows)
* [Password Flow](../authentication/password-flow)

If you want to retrieve data on behalf of your app, from a server, and not from an individual user's perspective, retrieve an App Access Token. This is the appropriate choice particularly for App Streams and notification servers.

* [App Access Token](../authentication/app-access-token)

## Fields

### Redirect URI

Redirect URIs can be any valid URL, including IP addresses, with ports, etc. It cannot contain a fragment.

If a query string is included on the redirect URI you specify in the Developer management area for your client, then pnut will only authorize that specific redirect URI. If you do not specify a query parameter, any query parameters will be allowed.

The special URI `urn:ietf:wg:oauth:2.0:oob` will redirect users to an HTML page where they can retrieve the access token for development purposes, or to manually enter it into your app.


### Selective Revocation & Token Groups

Users can deauthorize tokens for your app by the IP address used, the token group, or all tokens at once.

Token groups are optional. To specify a name to group a new token with, include `?token_group={name}` in your authorization or authentication call in the web or password flows. If implementing this feature, you may want to allow users to specify the name themselves, or create a unique group name for your device, if you can determine the device to be the same.

The name is limited to 64 bytes.