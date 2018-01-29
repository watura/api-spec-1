### User Following


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> any</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/following [<i class="fas fa-paragraph"></i>](#get-users-id-following) {#get-users-id-following .endpoint}

Retrieve a list of user objects that the specified user is following.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-1) {#url-parameters-1}

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
"call for example 1"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> any</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/followers [<i class="fas fa-paragraph"></i>](#get-users-id-followers) {#get-users-id-followers .endpoint}

Retrieve a list of user objects that are following the specified user.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-2) {#url-parameters-2}

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
"call for example 2"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> follow</span><span class="method method-put">PUT</span> /users/<span class="call-param">{user_id}</span>/follow [<i class="fas fa-paragraph"></i>](#put-users-id-follow) {#put-users-id-follow .endpoint}

Follow a user.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-3) {#url-parameters-3}

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
"call for example 3"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> follow</span><span class="method method-delete">DELETE</span> /users/<span class="call-param">{user_id}</span>/follow [<i class="fas fa-paragraph"></i>](#delete-users-id-follow) {#delete-users-id-follow .endpoint}

Unfollow a user.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-4) {#url-parameters-4}

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
"call for example 4"
```