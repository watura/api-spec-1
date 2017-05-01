### App Streams

App streams are long-lasting connections between the API and your server, often for notifications and other applications that need instant updates.

You will need an [app token](../authentication/app-access-token) to use them.


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> app</span><span class="method method-get">GET</span> /streams [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-streams) {#get-streams .endpoint}

Get all app streams for the authenticated app.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/streams" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X GET
```

Returns a list of streams.

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {
      "id": "3",
      "object_types": [
        "post",
        "message",
        "channel_subscription",
        "bookmark",
        "follow",
        "mute",
        "block",
        "channel",
        "user",
        "message",
        "token"
      ],
      "type": "long_poll",
      "key": "4",
      "endpoint": "wss://stream.pnut.io/v0/app?key=4"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> app</span><span class="method method-get">GET</span> /streams/<span class="call-param">{stream_key}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-streams-id) {#get-streams-id .endpoint}

Get a specific app stream by its key.

##### URL Parameters

Name|Description
-|-
`stream_key`|Stream to retrieve

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/streams/4" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X GET
```

Returns the requested stream.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "3",
    "object_types": [
      "post",
      "message",
      "channel_subscription",
      "bookmark",
      "follow",
      "mute",
      "block",
      "channel",
      "user",
      "message",
      "token"
    ],
    "type": "long_poll",
    "key": "4",
    "endpoint": "wss://stream.pnut.io/v0/app?key=4"
  }
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> app</span><span class="method method-post">POST</span> /streams [<i class="fa fa-paragraph" aria-hidden="true"></i>](#post-streams) {#post-streams .endpoint}

Create an app stream for the authenticated app. Can create up to five (5) app streams.

Must have a Content-Type of `application/json`.

##### Post Parameters

Field|Type|Description
-|-|-
`type`|string|The only value currently allowed is `long_poll`
`object_types`|list|Comma-separated list of object types to listen for. Valid values are `post`, `bookmark`, `follow`, `mute`, `block`, `message`, `channel`, `channel_subscription`, `token`, and `user`.
`key`|string|Optional name for the stream, instead of an automatically assigned numeric key. Alphanumeric and underscore allowed, 32 characters, unique for this app.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/streams" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
    \"type\":\"long_poll\",
    \"object_types\":[
        \"post\",\"message\",\"channel_subscription\",\"bookmark\"
    ],
    \"key\":\"butterball\"
}" \
    -X POST
```

Returns the created stream.

```json
{
  "meta": {
    "code": 201
  },
  "data": {
    "type": "long_poll",
    "key": "butterball",
    "id": 4,
    "object_types": [
      "post",
      "message",
      "channel_subscription",
      "bookmark"
    ],
    "endpoint": "wss://stream.pnut.io/v0/app?key=butterball"
  }
}
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> app</span><span class="method method-put">PUT</span> /streams/<span class="call-param">{stream_key}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-streams-id) {#put-streams-id .endpoint}

Update an app stream. Note that, currently, any connected app streams will not be updated until the app disconnects and reconnects.

The only changeable field currently is `object_types`.

##### URL Parameters

Name|Description
-|-
`stream_key`|Stream to update

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/streams/butterball" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
    \"object_types\":[
        \"post\",\"message\",\"bookmark\"
    ]
}" \
    -X POST
```

Returns the updated stream.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "type": "long_poll",
    "key": "butterball",
    "id": "4",
    "object_types": [
      "post",
      "message",
      "bookmark"
    ],
    "endpoint": "wss://stream.pnut.io/v0/app?key=butterball"
  }
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> app</span><span class="method method-delete">DELETE</span> /streams [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-streams) {#delete-streams .endpoint}

Delete all app streams for the authorized app.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/streams" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE
```

Returns a list of deleted streams.

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {
      "id": "3",
      "object_types": [
        "post",
        "message",
        "channel_subscription",
        "bookmark",
        "follow",
        "mute",
        "block",
        "channel",
        "user",
        "message",
        "token"
      ],
      "type": "long_poll",
      "key": "4",
      "endpoint": "wss://stream.pnut.io/v0/app?key=4",
      "is_deleted": true
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> app</span><span class="method method-delete">DELETE</span> /streams/<span class="call-param">{stream_key}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-streams-id) {#delete-streams-id .endpoint}

Delete a specific app stream by its key.

##### URL Parameters

Name|Description
-|-
`stream_key`|Stream to delete

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/streams/butterball" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE
```

Returns the deleted stream.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "type": "long_poll",
    "key": "butterball",
    "id": "4",
    "object_types": [
      "post",
      "message",
      "bookmark"
    ],
    "endpoint": "wss://stream.pnut.io/v0/app?key=butterball",
    "is_deleted": true
  }
}
```