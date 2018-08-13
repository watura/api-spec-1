# Token

Interactions with the authenticated token


## <span class="endpoint-meta">any</span><span class="method method-get">GET</span> /token [&para;](#get-token) {#get-token .endpoint}

Retrieve an object with the currently authenticated token, username, and user ID.

Includes `data.email` if `email` scope is authorized.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/token" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the requested token

```json
"call for example 1"
```


## <span class="endpoint-meta">any</span><span class="method method-delete">DELETE</span> /token [&para;](#delete-token) {#delete-token .endpoint}

Delete the currently authenticated token.

Note that this only deletes the currently authenticated token, and the user will still not be required to reauthorize scopes in the future that have been authorized. For the user to revoke all access tokens for the client, they must do so manually from their account on pnut.io.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/token" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1" \
    -X DELETE
```

Returns the deleted token

```json
"call for example 2"
```