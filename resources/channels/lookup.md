### Channel Lookup

To only retrieve channels by certain types, include them in a comma-separated list in the query parameter like so: `channel_types=io.pnut.core.pm,com.example.site`.



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> messages</span><span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span> [<i class="fas fa-paragraph"></i>](#get-channels-id) {#get-channels-id .endpoint}

Retrieve a channel object.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters) {#url-parameters}

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
"call for example 1"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> messages</span><span class="method method-get">GET</span> /channels [<i class="fas fa-paragraph"></i>](#get-channels) {#get-channels .endpoint}

Retrieve a list of specified channel objects. Only returns the first 200 found.

##### Query String Parameters [<i class="fas fa-paragraph"></i>](#query-string-parameters) {#query-string-parameters}

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
"call for example 2"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-get">GET</span> /users/me/channels [<i class="fas fa-paragraph"></i>](#get-users-me-channels) {#get-users-me-channels .endpoint}

Retrieve a list of channels created by the authenticated user.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of channels

```json
"call for example 3"
```



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-get">GET</span> /users/me/channels/existing_pm [<i class="fas fa-paragraph"></i>](#get-users-me-channels-existing_pm) {#get-users-me-channels-existing_pm .endpoint}

Retrieve a Private Message channel for a set of users, if one exists.

##### Query String Parameters [<i class="fas fa-paragraph"></i>](#query-string-parameters) {#query-string-parameters}

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
"call for example 4"
```



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-get">GET</span> /users/me/channels/num_unread/pm [<i class="fas fa-paragraph"></i>](#get-users-me-channels-num_unread-pm) {#get-users-me-channels-num_unread-pm .endpoint}

Retrieve the number of unread private messages for the authenticated user.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels/num_unread/pm" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the number of unread channels

```json
"call for example 5"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-delete">DELETE</span> /users/me/channels/num_unread/pm [<i class="fas fa-paragraph"></i>](#delete-users-me-channels-num_unread-pm) {#delete-users-me-channels-num_unread-pm .endpoint}

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
"call for example 6"
```