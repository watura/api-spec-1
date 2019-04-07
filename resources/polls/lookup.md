# Poll Lookup

Endpoints:

* [Get a poll](#get-polls-id)
* [Get multiple polls](#get-polls)
* [Get the authenticated user's polls](#get-users-me-polls)
* [Get responses to the authenticated user's polls](#get-users-me-polls-responses)


## <span class="method method-get">GET</span> /polls/<span class="call-param">{poll_id}</span> {#get-polls-id .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">polls</span>

Retrieve a poll object.

### URL Parameters

Name|Description
-|-
`poll_id`|ID of the requested poll

### Query Parameters

Name|Description
-|-
`poll_token`|Required on private polls when you don't know or aren't guaranteed access

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/polls/1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the requested poll details

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...Poll Object..."}
}
```



## <span class="method method-get">GET</span> /polls {#get-polls .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">polls</span>

Retrieve a list of specified poll objects. Only returns the first 100 found.

If the polls need a `poll_token` to access, you may include them with query parameters in the pattern `?poll_token_{poll_id}=xxx&poll_token_{poll_id}=xxx`.

### Query String Parameters

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
{
    "meta": {
        "code": 200
    },
    "data": [
        {"...Poll Object..."},
        {"...Poll Object..."}
    ]
}
```



## <span class="method method-get">GET</span> /users/me/polls {#get-users-me-polls .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">polls</span>

Retrieve a list of polls created by the authenticated user.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/polls" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of polls

```json
{
    "meta": {
        "more": false,
        "code": 200,
        "min_id": "0",
        "max_id": "0"
    },
    "data": [
        {"...Poll Object..."},
        {"...Poll Object..."}
    ]
}
```


## <span class="method method-get">GET</span> /users/me/polls/responses {#get-users-me-polls-responses .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">polls</span>

Retrieve a list of responses to polls created by the authenticated user. This is a parallel to the `poll_response` user interaction.

### Query String Parameters

Name|Description
-|-
`ids`|Optional comma-separated list of poll IDs. If included, only poll responses to these polls will be returned

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/polls/responses" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of polls

```json
{
    "meta": {
        "more": false,
        "code": 200,
        "min_id": "0",
        "max_id": "0"
    },
    "data": [
        {"...Abbreviated Poll Object..."},
        {"...Abbreviated Poll Object..."}
    ]
}
```