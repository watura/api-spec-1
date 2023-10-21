# Per-Channel User Presence

Endpoints:

* [Get users present in a channel](#get-channels-id-presence)
* [Get a single user's presence in a channel](#get-users-id-presence-channels-id)
* [Update the authenticated user's presence in a channel](#put-users-me-presence-channels-id)

A user's presence can be set for a specific channel, separately from its [global User Presence](/docs/resources/users/presence). It functions identically, but there are no helpers for updating status from other endpoints.

Getting [users subscribed to a channel](/docs/resources/channels/subscribing#get-channels-id-subscribers) with `?include_presence=1` query parameter will include the users' channel presence on their user object instead of their global presence.


## <span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/presence {#get-channels-id-presence .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Retrieve all users' presence statuses that are not "offline".

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/582/presence" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of users' presences.

```json
{
    "meta": {
        "code": 200
    },
    "data": []
}
```


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/presence/channels/<span class="call-param">{channel_id}</span> {#get-users-id-presence-channels-id .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Retrieve a user's presence in a channel.

If the user has never set a presence, `last_seen_at` will not be set.

### URL Parameters

Name|Description
-|-
`user_id`|ID of the user to retrieve
`channel_id`|ID of the channel to check within

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/1/presence/channels/582" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a user's current presence.

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "avatar_image": "String",
        "id": "0",
        "last_seen_at": "ISO 8601 (Optional)",
        "name": "String (Optional)",
        "presence": "String",
        "username": "String"
    }
}
```


## <span class="method method-put">PUT</span> /users/me/presence/channels/<span class="call-param">{channel_id}</span> {#put-users-me-presence-channels-id .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Update a user's presence in a channel.

### PUT Parameters

Name|Description
-|-
`presence`|A string up to 100 unicode characters. If not set, or if it is set to `1`, it will be updated to `"online"`. A value of `"offline"` or `0` will delete the user's presence and remove them from the [list of users online](#get-channels-id-presence).
`expiration`|Unix timestamp for when the given presence should expire. Default is 15 minutes into the future. If set too far into the future, will set to the maximum of 7 days. If set to a past timestamp, will delete the user's presence.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/me/presence/channels/582" \
    -X PUT \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -d "presence=keeping my stick on the ice&expiration=1721702296" \
    -H "X-Pretty-Json: 1"
```

Returns the updated user presence.

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "avatar_image": "String",
        "id": "0",
        "last_seen_at": "ISO 8601 (Optional)",
        "name": "String (Optional)",
        "presence": "String",
        "username": "String"
    }
}
```
