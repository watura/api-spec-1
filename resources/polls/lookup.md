### Poll Lookup





#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> polls</span><span class="method method-get">GET</span> /polls/<span class="call-param">{poll_id}</span> [<i class="fas fa-paragraph"></i>](#get-polls-id) {#get-polls-id .endpoint}

Retrieve a poll object.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`poll_id`|ID of the requested poll

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/polls/1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the requested poll details

```json
"call for example 1"
```



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> polls</span><span class="method method-get">GET</span> /users/me/polls [<i class="fas fa-paragraph"></i>](#get-users-me-polls) {#get-users-me-polls .endpoint}

Retrieve a list of polls created by the authenticated user.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/polls" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of polls

```json
"call for example 2"
```