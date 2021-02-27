# Authentication Password Flow

## Setup

Password flow must be explicitly approved on a per-client basis, by a Pnut administrator.

Request access by E-mailing [support@pnut.io](mailto:support@pnut.io), telling what platform the app runs on, and the client ID. If access is granted, you will be able to get your `password_grant_secret` from the client settings in the developer area.

__Do not save the user's password.__ You should take every measure to respect the user's security.

Where another flow is practical, use it. For your own projects and single-instance clients, you can authorize and retrieve a token for yourself directly from the client's developer page, or you can use web flows.

__You must__ display the scopes that you will be authorizing, somewhere before users login, even if on a linked section of your app.


## Process

Retrieve the user's username or E-mail address, and password, directly from them.

Now make a <span class="method method-post">POST</span> call with what you now have:

```bash
curl "https://api.pnut.io/v1/oauth/access_token" \
  -d "client_id=[client ID]" \
  -d "password_grant_secret=[stand-in for the client secret]" \
  -d "username=[username or E-mail address]" \
  -d "password=[account password OR one-time use password]" \
  -d "grant_type=password" \
  -d "scope=[comma-delimited scopes]" \
  -X POST
```

A JSON response will be returned in the form of:

```json
{"access_token":ACCESS_TOKEN, "token":{"...Token object..."}, "user_id":USER_ID, "username":USERNAME}
```

Every time a user is authorized using the password flow, they are sent an E-mail saying what client they were authorized for and what scopes.