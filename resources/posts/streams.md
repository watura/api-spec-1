# Post Streams

Endpoints:

* [Get a user's personal stream](#get-posts-streams-me)
* [Get a user's unified personal stream](#get-posts-streams-unified)
* [Get mentions of a user](#get-users-id-mentions)
* [Get posts by a user](#get-users-id-posts)
* [Get the global stream](#get-posts-streams-global)
* [Get posts with a tag](#get-posts-tags-tag)


## <span class="method method-get">GET</span> /posts/streams/me {#get-posts-streams-me .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">stream</span>

The authenticated user's stream of posts from their followers and themself.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/posts/streams/me?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
{
    "meta": {
        "more": true,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...Post Object..."},
        {"...Post Object..."}
    ]
}
```


## <span class="method method-get">GET</span> /posts/streams/unified {#get-posts-streams-unified .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">stream</span>

A combined Personal Stream including the authenticated user's mentions.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/posts/streams/unified?count=1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
{
    "meta": {
        "more": true,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...Post Object..."}
    ]
}
```


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/mentions {#get-users-id-mentions .endpoint}

Scope: <span class="endpoint-meta">none</span>

Posts mentioning the specified user.

### URL Parameters

Name|Description
-|-
`user_id`|Posts mention this user

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/9/mentions?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
{
    "meta": {
        "more": true,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"....Post Object..."},
        {"....Post Object..."}
    ]
}
```


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/posts {#get-users-id-posts .endpoint}

Scope: <span class="endpoint-meta">none</span>

Posts created by the specified user.

If a user looks up a user they blocked or muted, the posts will still be retrieved.

### URL Parameters

Name|Description
-|-
`user_id`|Posts created by this user

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/9/posts?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
{
    "meta": {
        "more": true,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...Post Object...."},
        {"...Post Object...."}
    ]
}
```


## <span class="method method-get">GET</span> /posts/streams/global {#get-posts-streams-global .endpoint}

Scope: <span class="endpoint-meta">none</span>

A stream of all `human`-type users' public posts.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/posts/streams/global?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
{
    "meta": {
        "more": true,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...Post Object.."},
        {"...Post Object.."}
    ]
}
```


## <span class="method method-get">GET</span> /posts/tags/<span class="call-param">{tag}</span> {#get-posts-tags-tag .endpoint}

Scope: <span class="endpoint-meta">none</span>

A stream of all posts that include the specified `tag`.

### URL Parameters

Name|Description
-|-
`tag`|The string tag that all posts should include

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/posts/tags/MondayNightDanceParty?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
{
    "meta": {
        "more": true,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"....Post Object...."},
        {"....Post Object...."}
    ]
}
```