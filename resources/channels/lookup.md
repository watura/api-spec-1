# Channel Lookup

*To only retrieve channels by certain types, include them in a comma-separated list in the query parameter like so: `channel_types=io.pnut.core.pm,com.example.site`.*

Endpoints:

* [Get a channel](#get-channels-id)
* [Get multiple channels](#get-channels)
* [Get the authenticated user's created channels](#get-users-me-channels)
* [Get a PM channel between users](#get-users-me-channels-existing_pm)
* [Get the number of channels unread by the authenticated user](#get-users-me-channels-num_unread)
* [Set all channels 'read'](#delete-users-me-channels-num_unread)


## <span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span> {#get-channels-id .endpoint}

Scope: <span class="endpoint-meta">messages</span>

Retrieve a channel object.

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the requested channel

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/5" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the requested channel

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...Channel Object..."}
}
```


## <span class="method method-get">GET</span> /channels {#get-channels .endpoint}

Scope: <span class="endpoint-meta">messages</span>

Retrieve a list of specified channel objects. Only returns the first 200 found.

### Query String Parameters

Name|Description
-|-
`ids`|Comma-separated list of channel IDs

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels?ids=3,4,16" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of channels

```json
{
    "meta": {
        "code": 200
    },
    "data": [
        {"...Channel Object..."},
        {"...Channel Object..."},
        {"...Channel Object..."}
    ]
}
```


## <span class="method method-get">GET</span> /users/me/channels {#get-users-me-channels .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Retrieve a list of channels created by the authenticated user.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/me/channels" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of channels

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



## <span class="method method-get">GET</span> /users/me/channels/existing_pm {#get-users-me-channels-existing_pm .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Retrieve a Private Message channel for a set of users, if one exists.

### Query String Parameters

Name|Description
-|-
`ids`|Comma-separated list of User IDs or @-usernames. The authenticated user can be included or excluded.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/me/channels/existing_pm?ids=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a channel.

```json
{
    "meta": {
        "code": 200
    },
    "data": {"....Channel Object..."}
}
```



## <span class="method method-get">GET</span> /users/me/channels/num_unread {#get-users-me-channels-num_unread .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Retrieve the number of unread messages for the authenticated user.

### Query String Parameters

Name|Description
-|-
`channel_types`|Comma-separated list of channel types to look up. Up to 4 at a time. Defaults to `io.pnut.core.pm`

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/me/channels/num_unread?channel_types=io.pnut.core.pm" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns an array of all the channel types requested, with their corresponding number of unread messages.

```json
{
    "meta": {
        "code": 200
    },
    "data": {
    	"io.pnut.core.pm": 2
    }
}
```


## <span class="method method-delete">DELETE</span> /users/me/channels/num_unread {#delete-users-me-channels-num_unread .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Mark all unread messages as read for the specified channel types for the authenticated user.

### Query String Parameters

Name|Description
-|-
`channel_types`|Comma-separated list of channel types to mark as read. Up to 4 at a time. Defaults to `io.pnut.core.pm`

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/me/channels/num_unread?channel_types=io.pnut.core.pm" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns an array of the channel types and their new count of `0`.

```json
{
    "meta": {
        "code": 200
    },
    "data": {
    	"io.pnut.core.pm": 0
    }
}
```