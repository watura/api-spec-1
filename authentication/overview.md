### Authentication

pnut.io implements parts of the [OAuth 2.0 standard](https://oauth.net/2/) to secure access between clients, users, and the API.

To authenticate and retrieve an app token or a token on behalf of a user, you will need to have an active client.

*If you are not a developer proper, you may create one client that only you can authorize (for all intents and purposes, only you can use it).*

*To become a developer, E-mail [support@pnut.io](mailto:support@pnut.io).*

Once you have created a client from the [Develop frontpage](https://pnut.io/dev), read through the implementation details and choose what [Scopes](../authentication/scope) you will need to authorize, and an appropriate Flow to authorize them with:

* [Web Flows](../authentication/web-flows)
* [Password Flow](../authentication/password-flow)

If you want to retrieve data on behalf of your app, from a server, and not from an individual user's perspective, retrieve an App Access Token. This is the appropriate choice particularly for App Streams and notification servers.

* [App Access Token](../authentication/app-access-token)