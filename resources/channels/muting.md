# Channel Muting

Muting a channel prevents other users from being able to auto-subscribe you to that channel.

Endpoints:

* [Get the authenticated user's muted channels](#get-users-me-channels-muted)
* [Mute a channel](#put-channels-id-mute)
* [Unmute a channel](#delete-channels-id-mute)


## <span class="method method-get">GET</span> /users/me/channels/muted {#get-users-me-channels-muted .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Retrieve a list of channels the authenticated user has muted.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels/muted" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of muted channels.

```json
{
    "meta": {
        "more": false,
        "min_id": "0",
        "max_id": "0",
        "code": 200
    },
    "data": [
        {"...Channel Object..."}
    ]
}
```



## <span class="method method-put">PUT</span> /channels/<span class="call-param">{channel_id}</span>/mute {#put-channels-id-mute .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Mute subscriptions for a channel. Muting unsubscribes, if you were subscribed.

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the channel to mute.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/2/mute" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the muted channel.

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...Channel Object..."}
}
```



## <span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span>/mute {#delete-channels-id-mute .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Delete a subscription mute for a channel.

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the channel to unmute.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/4/mute" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the unmuted channel.

```json
{
    "meta": {
        "code": 200
    },
    "data": {"....Channel Object..."}
}
```