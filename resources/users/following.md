# User Following

Endpoints:

* [Get followed users](#get-users-id-following)
* [Get a user's followers](#get-users-id-followers)
* [Follow a user](#put-users-id-follow)
* [Unfollow a user](#delete-users-id-follow)


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/following {#get-users-id-following .endpoint}

Scope: <span class="endpoint-meta">any</span>

Retrieve a list of user objects that the specified user is following.

### URL Parameters {#url-parameters-1}

Name|Description
-|-
`user_id`|ID of the user whose following to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/3/following?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of users

```json
{
    "meta": {
        "more": false,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...User Object..."}
    ]
}
```


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/followers {#get-users-id-followers .endpoint}

Scope: <span class="endpoint-meta">any</span>

Retrieve a list of user objects that are following the specified user.

### URL Parameters {#url-parameters-2}

Name|Description
-|-
`user_id`|ID of the user whose followers to retrieve


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/@shawn/followers?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of users

```json
{
    "meta": {
        "more": false,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...User Object..."},
        {"...User Object..."}
    ]
}
```


## <span class="method method-put">PUT</span> /users/<span class="call-param">{user_id}</span>/follow {#put-users-id-follow .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">follow</span>

Follow a user.

### URL Parameters {#url-parameters-3}

Name|Description
-|-
`user_id`|ID of the user to follow


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/246/follow" \
    -X PUT \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the followed user

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...User Object..."}
}
```


## <span class="method method-delete">DELETE</span> /users/<span class="call-param">{user_id}</span>/follow {#delete-users-id-follow .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">follow</span>

Unfollow a user.

### URL Parameters {#url-parameters-4}

Name|Description
-|-
`user_id`|ID of the user to unfollow

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/246/follow" \
    -X DELETE \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the unfollowed user

```json
{
    "meta": {
        "code": 200
    },
    "data": {"....User Object..."}
}
```