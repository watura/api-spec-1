# Post Lookup

Endpoints:

* [Get a post](#get-posts-id)
* [Get multiple posts](#get-posts)
* [Get post revisions](#get-posts-id-revisions)


## <span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span> {#get-posts-id .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a post object.

### URL Parameters

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
{
    "meta": {
        "code": 200
    },
    "data": {"...Post Object..."}
}
```


## <span class="method method-get">GET</span> /posts {#get-posts .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of specified post objects. Only retrieves the first 200 found.

### Query String Parameters

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
{
    "meta": {
        "code": 200
    },
    "data": [
        {"...Post Object..."},
        {"...Post Object..."},
        {"...Post Object..."}
    ]
}
```


## <span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span>/revisions {#get-posts-id-revisions .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of [previous versions](lifecycle#put-posts-id) of a post, not including the most recent. Currently a post can only have one previous version.

Revisions returned will have `revision` as a String number indicating which version of the post it is. Revisions start at `"0"`.

### URL Parameters

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
{
    "meta": {
        "code": 200
    },
    "data": [
        {"....Post Object..."}
    ]
}
```