# File Lookup

Endpoints:

* [Get a file](#get-files-id)
* [Get multiple files](#get-files)
* [Get the authenticated user's files](#get-users-me-files)


## <span class="method method-get">GET</span> /files/<span class="call-param">{file_id}</span> {#get-files-id .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">files</span>

Retrieve a file object. If `link_expires_at` is passed, this will update the `link` and any embedded references to it.

### URL Parameters

Name|Description
-|-
`file_id`|ID of the requested file

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/files/69" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the requested file details

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...File Object..."}
}
```


## <span class="method method-get">GET</span> /files {#get-files .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">files</span>

Retrieve a list of specified file objects. Only returns the first 200 found.

If the file need a `file_token_read` to access, you may include them with query parameters in the pattern `?file_token_read_{file_id}=xxx&file_token_read_{file_id}=xxx`.

### Query String Parameters

Name|Description
-|-
`ids`|Comma-separated list of file IDs

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/files?ids=69,71" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of files

```json
{
    "meta": {
        "code": 200
    },
    "data": [
        {"...File Object..."}
    ]
}
```


## <span class="method method-get">GET</span> /users/me/files {#get-users-me-files .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">files</span>

Retrieve a list of files created by the authenticated user.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/files" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of files

```json
{
    "meta": {
        "code": 200,
        "more": false,
        "max_id": "0",
        "min_id": "0"
    },
    "data": [
        {"...File Object..."}
    ]
}
```