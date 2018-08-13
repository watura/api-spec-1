# Messages Lookup



## <span class="endpoint-meta"><i class="fas fa-lock"></i> messages</span><span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span> [&para;](#get-channels-id-messages-id) {#get-channels-id-messages-id .endpoint}

Retrieve a message from a channel. The requesting user must have access to the channel or have created the message.

### URL Parameters [&para;](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the channel to retrieve a message from.
`message_id`|ID of the message to retrieve.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/messages/11" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the requested message.

```json
"call for example 1"
```



## <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span>/thread [&para;](#get-channels-id-messages-id-thread) {#get-channels-id-messages-id-thread .endpoint}

Retrieve messages in the same thread of a channel. All messages will have the same `thread_id` (they are all replies to the same post, or is not a reply to any post). The requesting user must have access to the channel.

### URL Parameters [&para;](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the channel to retrieve messages from.
`message_id`|ID of the message whose thread to retrieve.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/messages/13/thread" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of messages.

```json
"call for example 2"
```



## <span class="endpoint-meta"><i class="fas fa-lock"></i> messages</span><span class="method method-get">GET</span> /channels/messages [&para;](#get-messages) {#get-messages .endpoint}

Retrieve a list of specified messages. Will only return the first 200 found.

### Query String Parameters [&para;](#query-string-parameters) {#query-string-parameters}

Name|Description
-|-
`ids`|Comma-separated list of message IDs.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/messages?ids=4,11,12" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of the messages found.

```json
"call for example 3"
```


## <span class="endpoint-meta"><i class="fas fa-lock"></i> messages</span><span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/messages [&para;](#get-channels-id-messages) {#get-channels-id-messages .endpoint}

Retrieve paginated messages from a channel.

### URL Parameters [&para;](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`channel_id`|ID of the channel to retrieve messages from

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/2/messages" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of messages from the channel.

```json
"call for example 4"
```


## <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-get">GET</span> /users/me/messages [&para;](#get-users-me-messages) {#get-users-me-messages .endpoint}

Retrieve a paginated list of messages created by the authenticated user.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/messages" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of messages.

```json
"call for example 5"
```