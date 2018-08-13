# Post Streams



## <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> stream</span><span class="method method-get">GET</span> /posts/streams/me [&para;](#get-posts-streams-me) {#get-posts-streams-me .endpoint}

The authenticated user's stream of posts from their followers and themself.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/streams/me?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
"call for example 1"
```


## <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> stream</span><span class="method method-get">GET</span> /posts/streams/unified [&para;](#get-posts-streams-unified) {#get-posts-streams-unified .endpoint}

A combined Personal Stream including the authenticated user's mentions.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/streams/unified" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
"call for example 2"
```


## <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/mentions [&para;](#get-users-id-mentions) {#get-users-id-mentions .endpoint}

Posts mentioning the specified user.

### URL Parameters [&para;](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`user_id`|Posts mention this user

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/9/mentions?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
"call for example 3"
```


## <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/posts [&para;](#get-users-id-posts) {#get-users-id-posts .endpoint}

Posts created by the specified user.

If a user looks up a user they blocked or muted, the posts will still be retrieved.

### URL Parameters [&para;](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`user_id`|Posts created by this user

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/9/posts?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
"call for example 4"
```


## <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /posts/streams/global [&para;](#get-posts-streams-global) {#get-posts-streams-global .endpoint}

A stream of all users' public posts.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/streams/global?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
"call for example 5"
```


## <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /posts/tags/<span class="call-param">{tag}</span> [&para;](#get-posts-tags-tag) {#get-posts-tags-tag .endpoint}

A stream of all posts that include the specified `tag`.

### URL Parameters [&para;](#url-parameters-3) {#url-parameters-3}

Name|Description
-|-
`tag`|The string tag that all posts should include

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/tags/MondayNightDanceParty?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
"call for example 6"
```