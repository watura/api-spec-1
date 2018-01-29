### Post Threads


#### <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span>/thread [<i class="fas fa-paragraph"></i>](#get-posts-id-thread) {#get-posts-id-thread .endpoint}

Retrieve posts within a thread. Threads are separated by what root post all posts below it have replied to.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`post_id`|ID of the post to retrieve the thread for

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/18/thread" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts from the thread.

```json
"call for example 1"
```