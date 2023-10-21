# User Blocking

Endpoints:

* [Get blocked users](#get-users-id-blocked)
* [Block a user](#put-users-id-block)
* [Unblock a user](#delete-users-id-block)

Blocking a user prevents the blocked user and the blocking user from seeing each other on the network except in a few necessary places.


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/blocked {#get-users-id-blocked .endpoint}

Scope: <span class="endpoint-meta">any</span>

Retrieve a list of blocked users. Users may only see their own list of blocked users.

### URL Parameters

Name|Description
-|-
`user_id`|ID of the user whose list of blocked users to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/me/blocked" \
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


## <span class="method method-put">PUT</span> /users/<span class="call-param">{user_id}</span>/block {#put-users-id-block .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">follow</span>

Block a user. Blocked users will not show up in future requests, the same as if they were muted. Blocked users also cannot retrieve this authorized user in their requests. A user can block another user even if the other user is blocking them (but will only return an ID of the blocked user).

### URL Parameters

Name|Description
-|-
`user_id`|ID of the user to block

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/@testuser/block" \
    -X PUT \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the blocked user

```json
{
    "meta": {
        "code": 200
    },
    "data": {"....User Object..."}
}
```


## <span class="method method-delete">DELETE</span> /users/<span class="call-param">{user_id}</span>/block {#delete-users-id-block .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">follow</span>

Unblock a user. A user can unblock another user even if the other user is blocking them (but will only return an ID of the unblocked user).

### URL Parameters

Name|Description
-|-
`user_id`|ID of the user to unblock

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/@testuser/block" \
    -X DELETE \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the unblocked user

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...User Object...."}
}
```
