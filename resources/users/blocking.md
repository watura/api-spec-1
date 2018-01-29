### User Blocking

Blocking a user prevents the blocked user and the blocking user from seeing each other on the network except in a few necessary places.


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> any</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/blocked [<i class="fas fa-paragraph"></i>](#get-users-id-blocked) {#get-users-id-blocked .endpoint}

Retrieve a list of blocked users. Users may only see their own list of blocked users.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`user_id`|ID of the user whose list of blocked users to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/blocked" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of users

```json
"call for example 1"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> follow</span><span class="method method-put">PUT</span> /users/<span class="call-param">{user_id}</span>/block [<i class="fas fa-paragraph"></i>](#put-users-id-block) {#put-users-id-block .endpoint}

Block a user. Blocked users will not show up in future requests, the same as if they were muted. Blocked users also cannot retrieve this authorized user in their requests. Can do so even if the other user is blocking you (but will only return an ID of the blocked user).

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`user_id`|ID of the user to block

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/@testuser/block" \
    -X PUT \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the blocked user

```json
"call for example 2"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> follow</span><span class="method method-delete">DELETE</span> /users/<span class="call-param">{user_id}</span>/block [<i class="fas fa-paragraph"></i>](#delete-users-id-block) {#delete-users-id-block .endpoint}

Unblock a user. Can do so even if the other user is blocking you (but will only return an ID of the blocked user).

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-3) {#url-parameters-3}

Name|Description
-|-
`user_id`|ID of the user to unblock

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/@testuser/block" \
    -X DELETE \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the unblocked user

```json
"call for example 3"
```