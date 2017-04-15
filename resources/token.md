### Token

Interactions with the authenticated token


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> any</span><span class="method method-get">GET</span> /token [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-token) {#get-token .endpoint}

Retrieve an object with the currently authenticated token, username, and user ID.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/token" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns the requested token

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "app": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
    "scopes": [
      "follow",
      "write_post",
      "messages",
      "update_profile",
      "stream",
      "presence"
    ],
    "user": {...}
  }
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> any</span><span class="method method-delete">DELETE</span> /token [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-token) {#delete-token .endpoint}

Delete the currently authenticated token.

Note that this only deletes the currently authenticated token, and the user will still not be required to reauthorize scopes in the future that have been authorized. For the user to revoke all access tokens for the client, they must do so manually from their account on pnut.io.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/token" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE
```

Returns the deleted token

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "app": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
    "scopes": [
      "follow",
      "write_post",
      "messages",
      "update_profile",
      "stream",
      "presence"
    ],
    "user": {...}
  }
}
```