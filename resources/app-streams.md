### App Streams

App streams are long-lasting connections between the API and your server, often for notifications and other applications that need instant updates.

You will need an [app token](../authentication/app-access-token) to use them.


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> app</span><span class="method method-get">GET</span> /streams [<i class="fas fa-paragraph"></i>](#get-streams) {#get-streams .endpoint}

Get all app streams for the authenticated app.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/streams" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X GET \
    -H "X-Pretty-Json: 1"
```

Returns a list of streams.

```json
"call for example 1"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> app</span><span class="method method-get">GET</span> /streams/<span class="call-param">{stream_key}</span> [<i class="fas fa-paragraph"></i>](#get-streams-id) {#get-streams-id .endpoint}

Get a specific app stream by its key.

##### URL Parameters

Name|Description
-|-
`stream_key`|Stream to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/streams/4" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X GET \
    -H "X-Pretty-Json: 1"
```

Returns the requested stream.

```json
"call for example 2"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> app</span><span class="method method-post">POST</span> /streams [<i class="fas fa-paragraph"></i>](#post-streams) {#post-streams .endpoint}

Create an app stream for the authenticated app. Can create up to five (5) app streams.

Must have a Content-Type of `application/json`.

##### Post Parameters

Field|Type|Description
-|-|-
`type`|string|The only value currently allowed is `long_poll`
`object_types`|array|List of object types to listen for. Valid values are `post`, `bookmark`, `follow`, `mute`, `block`, `message`, `channel`, `channel_subscription`, `token`, `file`, and `user`.
`key`|string|Optional name for the stream, instead of an automatically assigned numeric key. Alphanumeric and underscore allowed, 32 characters, unique for this app.

##### Example {.example-code}

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
    -X POST \
    -H "X-Pretty-Json: 1"
```

Returns the created stream.

```json
"call for example 3"
```



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> app</span><span class="method method-put">PUT</span> /streams/<span class="call-param">{stream_key}</span> [<i class="fas fa-paragraph"></i>](#put-streams-id) {#put-streams-id .endpoint}

Update an app stream. Note that, currently, any connected app streams will not be updated until the app disconnects and reconnects.

The only changeable field currently is `object_types`.

##### URL Parameters

Name|Description
-|-
`stream_key`|Stream to update

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/streams/butterball" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
    \"object_types\":[
        \"post\",\"message\",\"bookmark\"
    ]
}" \
    -X POST \
    -H "X-Pretty-Json: 1"
```

Returns the updated stream.

```json
"call for example 4"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> app</span><span class="method method-delete">DELETE</span> /streams [<i class="fas fa-paragraph"></i>](#delete-streams) {#delete-streams .endpoint}

Delete all app streams for the authorized app.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/streams" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns a list of deleted streams.

```json
"call for example 5"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> app</span><span class="method method-delete">DELETE</span> /streams/<span class="call-param">{stream_key}</span> [<i class="fas fa-paragraph"></i>](#delete-streams-id) {#delete-streams-id .endpoint}

Delete a specific app stream by its key.

##### URL Parameters

Name|Description
-|-
`stream_key`|Stream to delete

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/streams/butterball" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the deleted stream.

```json
"call for example 6"
```