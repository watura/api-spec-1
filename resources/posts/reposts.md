### Reposts

Reposting is a special action. Reposts act as complete posts in themselves, with the "original" post embedded as an additional object. Unlike normal posts, actions (reply, repost, bookmark) cannot be executed against a repost.

#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> write_post</span><span class="method method-put">PUT</span> /posts/<span class="call-param">{post_id}</span>/repost [<i class="fas fa-paragraph"></i>](#put-posts-id-repost) {#put-posts-id-repost .endpoint}

Repost another post. The repost will show up in followers' streams if they have not seen another repost of the same within the last week, and if the reposted post is not in their recent stream. It is created in its own thread, not the thread of the original post. This increments a user's post count.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters) {#url-parameters}

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
"call for example 1"
```    


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> write_post</span><span class="method method-delete">DELETE</span> /posts/<span class="call-param">{post_id}</span>/repost [<i class="fas fa-paragraph"></i>](#delete-posts-id-repost) {#delete-posts-id-repost .endpoint}

Delete a repost. The actual repost is completely deleted; it does not leave behind a thread or deleted post to look up.

Users can also delete their own reposts even if they no longer have access to the original post (e.g., they were blocked). In that case, the returned post in the `data` field is simply `{"id":POST_ID,"you_reposted":false}`.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-1) {#url-parameters-1}

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
"call for example 2"
```