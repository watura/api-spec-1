# App Access Token

## Setup

App access tokens can only be retrieved by developers' apps.

All that is required is the `client_id` and `client_secret`.

App tokens are only to be used server-side, in ways that will protect the data. They can retrieve any data that any authorized users of the app can access, so you must take care to respect users' blocks and mutes yourself.


## Process

Make a <span class="method method-post">POST</span> call like so:

```bash
curl "https://api.pnut.io/v0/oauth/access_token" \
  -d "client_id=[client ID]" \
  -d "client_secret=[client secret]" \
  -d "grant_type=client_credentials" \
  -X POST
```

A JSON response will be returned in the form of:

```json
{"access_token":ACCESS_TOKEN, "token":{...}}
```


These are the endpoints available to app tokens, in addition to any endpoints that do not require authentication:

* GET /users/{user_id}/following
* GET /users/{user_id}/followers
* GET /users/{user_id}/muted
* GET /channels
* GET /channels/{channel_id}
* GET /channels/{channel_id}/subscribers
* GET /channels/{channel_id}/messages
* GET /channels/{channel_id}/messages/{message_id}
* GET /channels/messages
* POST /streams
* GET /streams/{stream_key}
* PUT /streams/{stream_key}
* DELETE /streams/{stream_key}
* GET /streams
* DELETE /streams
* GET /apps/me/users/ids
* GET /apps/me/users/tokens