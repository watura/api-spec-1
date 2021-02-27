# Clients

Client name can contain any Unicode characters. *Be sure to escape it if necessary.*

Endpoints:

* [Get a user's clients](#get-users-id-clients)
* [Get a client](#get-clients-id)


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/clients {#get-users-id-clients .endpoint}

Scope: <span class="endpoint-meta">any</span>

Retrieve a list of active clients created by a user.

### URL Parameters

Name|Description
-|-
`user_id`|ID of the user to list clients from

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v1/users/8/clients" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of clients

```json
{
    "meta": {
        "code": 200
    },
    "data": [
        {
            "id": "String",
            "name": "String",
            "url": "https://example.com"
        }
    ]
}
```


## <span class="method method-get">GET</span> /clients/<span class="call-param">{client_id}</span> {#get-clients-id .endpoint}

Scope: <span class="endpoint-meta">any</span>

Retrieve details on a public client, by client ID.

### URL Parameters

Name|Description
-|-
`client_id`|ID of the client to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/clients/3PFPMSet53RutGINA8e5HWqYg_UCDHad" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the detailed client object

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "created_at": "ISO-8601",
        "user": {"...User Object..."},
        "id": "String",
        "url": "https://example.com",
        "logo_image": "https://example.com/logo.png",
        "name": "String",
        "posts": 0,
        "content": {
            "text": "String",
            "html": "<span itemscope=\"https://pnut.io/schemas/Post\">String</span>",
            "entities": {
                "links": [],
                "mentions": [],
                "tags": []
            }
        }
    }
}
```