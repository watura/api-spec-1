### Post Threads


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span>/thread [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts-id-thread) {#get-posts-id-thread .endpoint}

Retrieve posts within a thread. Threads are separated by what root post all posts below it have replied to.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`post_id`|ID of the post to retrieve the thread for

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/20/thread" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts from the thread.

```json

```