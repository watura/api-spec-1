# Channel Subscribing

Subscribed channels act like an "inbox" of channels ordered by their most recent messages.

Endpoints:

* [Get the authenticated user's subscribed channels](#get-users-me-channels-subscribed)
* [Get users subscribed to a channel](#get-channels-id-subscribers)
* [Subscribe to a channel](#put-channels-id-subscribe)
* [Unsubscribe from a channel](#delete-channels-id-subscribe)


## <span class="method method-get">GET</span> /users/me/channels/subscribed {#get-users-me-channels-subscribed .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Retrieve a list of channels the authenticated user is subscribed to.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels/subscribed" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of subscribed channels.

```json
"call for example 1"
```



## <span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/subscribers {#get-channels-id-subscribers .endpoint}

Scope: <span class="endpoint-meta">messages</span>

Retrieve a list of users subscribed to a channel.

### URL Parameters [&para;](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the channel retrieve subscribers for.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/18/subscribers" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of users.

```json
"call for example 2"
```



## <span class="method method-put">PUT</span> /channels/<span class="call-param">{channel_id}</span>/subscribe {#put-channels-id-subscribe .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Subscribe to updates from a channel. Subscribing unmutes it, if you were muting it.

### URL Parameters [&para;](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`channel_id`|ID of the channel to subscribe to.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/18/subscribe" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the subscribed channel.

```json
"call for example 3"
```



## <span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span>/subscribe {#delete-channels-id-subscribe .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Delete a subscription for a channel. Unsubscribing also deletes any existing stream marker for the channel.

### URL Parameters [&para;](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`channel_id`|ID of the channel to unsubscribe from.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/18/subscribe" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the unsubscribed channel.

```json
"call for example 4"
```