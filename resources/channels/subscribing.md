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
curl "https://api.pnut.io/v1/users/me/channels/subscribed" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of subscribed channels.

```json
{
    "meta": {
        "more": false,
        "max_id": "0",
        "min_id": "0",
        "unread_counts": {
            "io.pnut.core.chat": 0,
            "io.pnut.core.pm": 0
        },
        "code": 200
    },
    "data": [
        {"...Channel Object..."}
    ]
}
```



## <span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/subscribers {#get-channels-id-subscribers .endpoint}

Scope: <span class="endpoint-meta">messages</span>

Retrieve a list of users subscribed to a channel.

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the channel retrieve subscribers for.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/18/subscribers" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of users.

```json
{
    "meta": {
        "code": 200
    },
    "data": [
        {"...User Object..."}
    ]
}
```



## <span class="method method-put">PUT</span> /channels/<span class="call-param">{channel_id}</span>/subscribe {#put-channels-id-subscribe .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Subscribe to updates from a channel. Subscribing unmutes it, if you were muting it.

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the channel to subscribe to.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/18/subscribe" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the subscribed channel.

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...Channel Object..."}
}
```



## <span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span>/subscribe {#delete-channels-id-subscribe .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Delete a subscription for a channel. Unsubscribing also deletes any existing stream marker for the channel.

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the channel to unsubscribe from.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/18/subscribe" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the unsubscribed channel.

```json
{
    "meta": {
        "code": 200
    },
    "data": {"....Channel Object..."}
}
```