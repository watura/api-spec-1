# Poll Lookup





## <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> polls</span><span class="method method-get">GET</span> /polls/<span class="call-param">{poll_id}</span> [&para;](#get-polls-id) {#get-polls-id .endpoint}

Retrieve a poll object.

### URL Parameters [&para;](#url-parameters) {#url-parameters}

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



## <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> polls</span><span class="method method-get">GET</span> /polls [&para;](#get-polls) {#get-polls .endpoint}

Retrieve a list of specified poll objects. Only returns the first 100 found.

If the polls need a `poll_token` to access, you may include them with query parameters in the pattern `?poll_token_{poll_id}=xxx&poll_token_{poll_id}=xxx`.

### Query String Parameters [&para;](#query-string-parameters) {#query-string-parameters}

Name|Description
-|-
`ids`|Comma-separated list of poll IDs

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/polls?ids=1,12" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of polls

```json
"call for example 2"
```



## <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> polls</span><span class="method method-get">GET</span> /users/me/polls [&para;](#get-users-me-polls) {#get-users-me-polls .endpoint}

Retrieve a list of polls created by the authenticated user.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/polls" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of polls

```json
"call for example 3"
```