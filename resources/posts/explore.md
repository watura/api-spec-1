# Explore Streams

Explore streams are basically pre-built searches with some simple criteria.

Endpoints:

* [Get a list of explore streams](#get-posts-streams-explore)
* [Get an explore stream](#get-posts-streams-explore-slug)


## <span class="method method-get">GET</span> /posts/streams/explore {#get-posts-streams-explore .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of explore streams.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/streams/explore" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of explore streams.

```json
{
    "meta": {
        "code": 200
    },
    "data": [
        {
            "description": "String",
            "link": "https://example.com",
            "slug": "String",
            "title": "String"
        }
    ]
}
```


## <span class="method method-get">GET</span> /posts/streams/explore/<span class="call-param">{slug}</span> {#get-posts-streams-explore-slug .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of posts in an explore stream.

### URL Parameters

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