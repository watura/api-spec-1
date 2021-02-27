# Post Threads

Post thread is determined by the post that is not a reply. A reply to a reply will not create a new "thread" in the API.

*If looking for how to retrieve only replies to a specific post, use [post search](search).*

Endpoints:

* [Get posts in a thread](#get-posts-id-thread)


## <span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span>/thread {#get-posts-id-thread .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve posts within a thread. Threads are separated by what root post all posts below it have replied to.

### URL Parameters

Name|Description
-|-
`post_id`|ID of the post to retrieve the thread for

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/posts/18/thread" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts from the thread.

```json
{
    "meta": {
        "more": false,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...Post Object..."}
    ]
}
```