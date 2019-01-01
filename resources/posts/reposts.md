# Reposts

Reposting is a special action. Reposts act as complete posts in themselves, with the "original" post embedded as an additional object. Unlike normal posts, actions (reply, repost, bookmark) cannot be executed against a repost.

Endpoints:

* [Create a Repost](#put-posts-id-repost)
* [Delete a repost](#delete-posts-id-repost)


## <span class="method method-put">PUT</span> /posts/<span class="call-param">{post_id}</span>/repost {#put-posts-id-repost .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">write_post</span>

Repost another post. The repost will show up in followers' streams if they have not seen another repost of the same within the last week, and if the reposted post is not in their recent stream. It is created in its own thread, not the thread of the original post. This increments a user's post count.

### URL Parameters

Name|Description
-|-
`post_id`|ID of the post to repost

##### Example {.example-code}
        
```bash
curl "https://api.pnut.io/v0/posts/2370/repost" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the reposted post.

```json
{
    "meta": {
        "code": 201
    },
    "data": {"...Post object..."}
}
```    


## <span class="method method-delete">DELETE</span> /posts/<span class="call-param">{post_id}</span>/repost {#delete-posts-id-repost .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">write_post</span>

Delete a repost. The actual repost is completely deleted; it does not leave behind a thread or deleted post to look up.

Users can also delete their own reposts even if they no longer have access to the original reposted post (e.g., they were blocked). In that case, the returned post in the `data` field is simply `{"id":POST_ID,"you_reposted":false}`.

### URL Parameters

Name|Description
-|-
`post_id`|ID of the post to delete a repost for

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/2370/repost" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the previously reposted post.

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...Post object..."}
}
```