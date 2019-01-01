# Channel Lookup

To only retrieve channels by certain types, include them in a comma-separated list in the query parameter like so: `channel_types=io.pnut.core.pm,com.example.site`.

Endpoints:

* [Get a channel](#get-channels-id)
* [Get multiple channels](#get-channels)
* [Get the authenticated user's created channels](#get-users-me-channels)
* [Get a PM channel between users](#get-users-me-channels-existing_pm)
* [Get the number of PM channels unread by the authenticated user](#get-users-me-channels-num_unread-pm)
* [Set all PM channels 'read'](#delete-users-me-channels-num_unread-pm)


## <span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span> {#get-channels-id .endpoint}

Scope: <span class="endpoint-meta">messages</span>

Retrieve a channel object.

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the requested channel

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5" \
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
curl "https://api.pnut.io/v0/channels?ids=3,4,16" \
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
curl "https://api.pnut.io/v0/users/me/channels" \
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
curl "https://api.pnut.io/v0/users/me/channels/existing_pm?ids=2" \
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



## <span class="method method-get">GET</span> /users/me/channels/num_unread/pm {#get-users-me-channels-num_unread-pm .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Retrieve the number of unread private messages for the authenticated user.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels/num_unread/pm" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the number of unread channels

```json
{
    "meta": {
        "code": 200
    },
    "data": 0
}
```


## <span class="method method-delete">DELETE</span> /users/me/channels/num_unread/pm {#delete-users-me-channels-num_unread-pm .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Mark all unread private messages as read for the authenticated user.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels/num_unread/pm" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the number of unread channels (`0`)

```json
{
    "meta": {
        "code": 200
    },
    "data": 0
}
```