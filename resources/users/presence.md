# User Presence

A user's presence is the recent status of that user. Each updated presence lasts for 15 minutes, or until another status is given. Users who do not have a current status show up as "offline".

A user's status can be updated on *any* authenticated call by simply including the `update_presence` query parameter with a status for its value. If this method is attempted, the response's `meta.updated_presence` key will be set and `true`. If it fails to update, it will be `false`.

Endpoints:

* [Get present users](#get-presence)
* [Get a user's presence](#get-users-id-presence)
* [Update user presence](#put-users-id-presence)


## <span class="method method-get">GET</span> /presence {#get-presence .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Retrieve all users' presence statuses that are not "offline".

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/presence" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of users' presences.

```json
"call for example 1"
```


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/presence {#get-users-id-presence .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Retrieve a user's presence.

If the user has never set a presence, `last_seen_at` will not be set.

### URL Parameters [&para;](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`user_id`|ID of the user to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/1/presence" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a user's current presence.

```json
"call for example 2"
```


## <span class="method method-put">PUT</span> /users/<span class="call-param">{user_id}</span>/presence {#put-users-id-presence .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">presence</span>

Update a user's presence.

If the `update_presence` query parameter is set on this call, it will override this call. It will not occur twice.

### URL Parameters [&para;](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`user_id`|ID of the user presence to update

### PUT Parameters [&para;](#put-parameters-1) {#put-parameters-1}

Name|Description
-|-
`presence`|A string up to 100 unicode characters. If not set, or if it is set to `1`, it will be updated to `"online"`. A value of `"offline"` or `0` will delete the user's presence and remove them from the [list of users online](#get-presence).

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/presence" \
    -X PUT \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -d "presence=keeping my stick on the ice" \
    -H "X-Pretty-Json: 1"
```



```json
"call for example 3"
```