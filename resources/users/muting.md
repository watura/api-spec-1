# User Muting

Endpoints:

* [Get muted users](#get-users-id-muted)
* [Mute a user](#put-users-id-mute)
* [Unmute a user](#delete-users-id-mute)

Muting a user will prevent them from being visible to the muting user unless specifically requested.


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/muted {#get-users-id-muted .endpoint}

Scope: <span class="endpoint-meta">any</span>

Retrieve a list of muted users. Users may only see their own list of muted users.

### URL Parameters

Name|Description
-|-
`user_id`|ID of the user whose list of muted users to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/me/muted" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of users

```json
{
    "meta": {
        "more": false,
        "code": 200
    },
    "data": [
        {"...User Object..."}
    ]
}
```


## <span class="method method-put">PUT</span> /users/<span class="call-param">{user_id}</span>/mute {#put-users-id-mute .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">follow</span>

Mute a user. Muted users will not appear in future requests.

### URL Parameters

Name|Description
-|-
`user_id`|ID of the user to mute

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/@testuser/mute" \
    -X PUT \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the muted user

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...User Object..."}
}
```


## <span class="method method-delete">DELETE</span> /users/<span class="call-param">{user_id}</span>/mute {#delete-users-id-mute .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">follow</span>

Unmute a user.

### URL Parameters

Name|Description
-|-
`user_id`|ID of the user to unmute

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/@testuser/mute" \
    -X DELETE \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the unmuted user

```json
{
    "meta": {
        "code": 200
    },
    "data": {"....User Object..."}
}
```
