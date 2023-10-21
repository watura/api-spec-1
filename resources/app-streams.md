# App Streams

Endpoints:

* [Get all streams](#get-streams)
* [Get a stream](#get-streams-id)
* [Create a stream](#post-streams)
* [Update a stream](#put-streams-id)
* [Delete all streams](#delete-streams)
* [Delete a stream](#delete-streams-id)

App streams are long-lasting connections between the API and your server, often for notifications and other applications that need instant updates.

You will need an [app token](../authentication/app-access-token) to use them. Look at [How To: App Streams](../how-to/app-streams) for details on usage.


## <span class="method method-get">GET</span> /streams {#get-streams .endpoint}

Token: <span class="endpoint-meta">app</span>

Get all app streams for the authenticated app.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/streams" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X GET \
    -H "X-Pretty-Json: 1"
```

Returns a list of streams.

```json
{
    "meta": {
        "code": 200
    },
    "data": [
        {
            "key": "String",
            "object_types": [
                "String",
                "String",
                "String"
            ],
            "endpoint": "wss://stream.pnut.io/v1/app",
            "type": "long_poll"
        }
    ]
}
```


## <span class="method method-get">GET</span> /streams/<span class="call-param">{stream_key}</span> {#get-streams-id .endpoint}

Token: <span class="endpoint-meta">app</span>

Get a specific app stream by its key.

### URL Parameters

Name|Description
-|-
`stream_key`|Stream to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/streams/4" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X GET \
    -H "X-Pretty-Json: 1"
```

Returns the requested stream.

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "key": "String",
        "object_types": [
            "String",
            "String",
            "String"
        ],
        "endpoint": "wss://stream.pnut.io/v1/app",
        "type": "long_poll"
    }
}
```


## <span class="method method-post">POST</span> /streams {#post-streams .endpoint}

Token: <span class="endpoint-meta">app</span>

Create an app stream for the authenticated app. Can create up to five (5) app streams.

Must have a Content-Type of `application/json`.

### Post Parameters

Field|Type|Description
-|-|-
`type`|string|The only value currently allowed is `long_poll`
`object_types`|array|List of object types to listen for. Valid values are `post`, `bookmark`, `follow`, `mute`, `block`, `message`, `channel`, `channel_subscription`, `token`, `file`, `poll`, `user_presence`, `user_channel_presence`, and `user`.
`key`|string|Optional name for the stream, instead of an automatically assigned numeric key. Alphanumeric and underscore allowed, 32 characters, unique for this app.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/streams" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
    \"type\":\"long_poll\",
    \"object_types\":[
        \"post\",\"message\",\"channel_subscription\",\"bookmark\"
    ],
    \"key\":\"butterball\"
}" \
    -X POST \
    -H "X-Pretty-Json: 1"
```

Returns the created stream.

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "key": "String",
        "object_types": [
            "String",
            "String",
            "String"
        ],
        "endpoint": "wss://stream.pnut.io/v1/app",
        "type": "long_poll"
    }
}
```



## <span class="method method-put">PUT</span> /streams/<span class="call-param">{stream_key}</span> {#put-streams-id .endpoint}

Token: <span class="endpoint-meta">app</span>

Update an app stream. Note that, currently, any connected app streams will not be updated until the app disconnects and reconnects.

The only changeable field currently is `object_types`.

### URL Parameters

Name|Description
-|-
`stream_key`|Stream to update

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/streams/butterball" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
    \"object_types\":[
        \"post\",\"message\",\"bookmark\"
    ]
}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the updated stream.

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "key": "String",
        "object_types": [
            "String"
        ],
        "endpoint": "wss://stream.pnut.io/v1/app",
        "type": "long_poll"
    }
}
```


## <span class="method method-delete">DELETE</span> /streams {#delete-streams .endpoint}

Token: <span class="endpoint-meta">app</span>

Delete all app streams for the authorized app.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/streams" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns a list of deleted streams.

```json
{
    "meta": {
        "code": 200
    },
    "data": [
        {
            "key": "String",
            "object_types": [
                "String",
                "String"
            ],
            "endpoint": "wss://stream.pnut.io/v1/app",
            "type": "long_poll",
            "is_deleted": true
        }
    ]
}
```


## <span class="method method-delete">DELETE</span> /streams/<span class="call-param">{stream_key}</span> {#delete-streams-id .endpoint}

Token: <span class="endpoint-meta">app</span>

Delete a specific app stream by its key.

### URL Parameters

Name|Description
-|-
`stream_key`|Stream to delete

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/streams/butterball" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the deleted stream.

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "key": "String",
        "object_types": [
            "String",
            "String",
            "String"
        ],
        "endpoint": "wss://stream.pnut.io/v1/app",
        "type": "long_poll",
        "is_deleted": true
    }
}
```
