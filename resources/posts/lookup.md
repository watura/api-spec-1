### Post Lookup


#### <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span> [<i class="fas fa-paragraph"></i>](#get-posts-id) {#get-posts-id .endpoint}

Retrieve a post object.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`post_id`|Post to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/20" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a post

```json
"call for example 1"
```


#### <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /posts [<i class="fas fa-paragraph"></i>](#get-posts) {#get-posts .endpoint}

Retrieve a list of specified post objects. Only retrieves the first 200 found.

##### Query String Parameters [<i class="fas fa-paragraph"></i>](#query-string-parameters) {#query-string-parameters}

Name|Description
-|-
`ids`|Comma-separated list of post IDs.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts?ids=20,21,4" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts

```json
"call for example 2"
```


#### <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span>/revisions [<i class="fas fa-paragraph"></i>](#get-posts-id-revisions) {#get-posts-id-revisions .endpoint}

Retrieve a list of [previous versions](lifecycle#put-posts-id) of a post, not including the most recent. Currently a post can only have one previous version.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`post_id`|Post ID to retrieve any revisions of

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/2392/revisions" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts

```json
"call for example 3"
```