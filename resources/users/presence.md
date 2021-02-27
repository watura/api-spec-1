# User Presence

A user's presence is the recent status of that user. Each updated presence lasts for 15 minutes, or until another status is given. Users who do not have a current status show up as "offline".

A user's status can be updated on *any* authenticated call by simply including the `update_presence` query parameter with a status for its value. If this method is attempted, the response's `meta.updated_presence` key will be set and `true`. If it fails to update, it will be `false`.

Endpoints:

* [Get present users](#get-presence)
* [Get a user's presence](#get-users-id-presence)
* [Update the authenticated user's presence](#put-users-me-presence)


## <span class="method method-get">GET</span> /presence {#get-presence .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Retrieve all users' presence statuses that are not "offline".

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/presence" \
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


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/presence {#get-users-id-presence .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Retrieve a user's presence.

If the user has never set a presence, `last_seen_at` will not be set.

### URL Parameters

Name|Description
-|-
`user_id`|ID of the user to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/1/presence" \
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
        "last_seen_at": "ISO 8601",
        "name": "String",
        "presence": "String",
        "username": "String"
    }
}
```


## <span class="method method-put">PUT</span> /users/me/presence {#put-users-me-presence .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">presence</span>

Update a user's presence.

If the `update_presence` query parameter is set on this call, it will override this call. It will not occur twice.

### PUT Parameters

Name|Description
-|-
`presence`|A string up to 100 unicode characters. If not set, or if it is set to `1`, it will be updated to `"online"`. A value of `"offline"` or `0` will delete the user's presence and remove them from the [list of users online](#get-presence).

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/me/presence" \
    -X PUT \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -d "presence=keeping my stick on the ice" \
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
        "last_seen_at": "ISO 8601", 
        "name": "String",
        "presence": "String",
        "username": "String"
    }
}
```