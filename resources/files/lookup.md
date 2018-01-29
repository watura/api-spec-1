### File Lookup





#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> files</span><span class="method method-get">GET</span> /files/<span class="call-param">{file_id}</span> [<i class="fas fa-paragraph"></i>](#get-files-id) {#get-files-id .endpoint}

Retrieve a file object. If `link_expires_at` is passed, this will update the `link` and any embedded references to it.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters) {#url-parameters}

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
"call for example 1"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> files</span><span class="method method-get">GET</span> /files [<i class="fas fa-paragraph"></i>](#get-files) {#get-files .endpoint}

Retrieve a list of specified file objects. Only returns the first 200 found.

##### Query String Parameters [<i class="fas fa-paragraph"></i>](#query-string-parameters) {#query-string-parameters}

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
"call for example 2"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> files</span><span class="method method-get">GET</span> /users/me/files [<i class="fas fa-paragraph"></i>](#get-users-me-files) {#get-users-me-files .endpoint}

Retrieve a list of files created by the authenticated user.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/files" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of files

```json
"call for example 3"
```