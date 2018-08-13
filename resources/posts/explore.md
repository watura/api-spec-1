# Explore Streams

Explore streams are basically pre-built searches with some simple criteria.


## <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /posts/streams/explore [&para;](#get-posts-streams-explore) {#get-posts-streams-explore .endpoint}

Retrieve a list of explore streams.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/streams/explore" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of explore streams.

```json
"call for example 1"
```


## <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /posts/streams/explore/<span class="call-param">{slug}</span> [&para;](#get-posts-streams-explore-slug) {#get-posts-streams-explore-slug .endpoint}

Retrieve a list of posts in an explore stream.

### URL Parameters [&para;](#url-parameters) {#url-parameters}

Name|Description
-|-
`slug`|Slug of the stream to retrieve posts from. Retrieve slugs to use from the previous call.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/streams/explore/conversations?count=1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
"call for example 2"
```