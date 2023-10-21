# Token

Endpoints:

* [Get the current token](#get-token)
* [Delete the current token](#delete-token)

Get or delete the current user's authenticated token.


## <span class="method method-get">GET</span> /token {#get-token .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Retrieve an object with the currently authenticated token, username, and user ID.

Includes `data.email` if `email` scope is authorized. Includes `markdown_text` in user object.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/token" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the requested token

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "app": {
            "id": "String",
            "url": "https://example.com",
            "name": "String"
        },
        "scopes": [
            "String",
            "String",
            "String"
        ],
        "user": {"...User Object..."},
        "storage": {
            "available": 0,
            "total": 0
        }
    }
}
```


## <span class="method method-delete">DELETE</span> /token {#delete-token .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Delete the currently authenticated token.

Note that this only deletes the currently authenticated token, and the user will still not be required to reauthorize scopes in the future that have been authorized. For the user to revoke all access tokens for the client, they must do so manually from their account on pnut.io, or all of their tokens for the client must be deleted to reset scopes.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/token" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1" \
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
            "id": "String",
            "url": "https://example.com",
            "name": "String"
        },
        "scopes": [
            "String",
            "String",
            "String"
        ],
        "user": {"...User Object...."},
        "storage": {
            "available": 0,
            "total": 0
        }
    }
}
```
