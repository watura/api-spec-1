### Post Bookmarks

Bookmarking is an action for users to keep track of posts. You can see others' bookmarks as well.

#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> any</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/bookmarks [<i class="fas fa-paragraph"></i>](#get-users-id-bookmarks) {#get-users-id-bookmarks .endpoint}

Retrieve a list of bookmarks made by the specified user.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`user_id`|What user's bookmarks to look up

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/1/bookmarks" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

```json
"call for example 1"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> write_post</span><span class="method method-put">PUT</span> /posts/<span class="call-param">{post_id}</span>/bookmark [<i class="fas fa-paragraph"></i>](#put-posts-id-bookmark) {#put-posts-id-bookmark .endpoint}

Bookmark a post.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`post_id`|Post to bookmark

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/2375/bookmark" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the bookmarked post.

```json
"call for example 2"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> write_post</span><span class="method method-delete">DELETE</span> /posts/<span class="call-param">{post_id}</span>/bookmark [<i class="fas fa-paragraph"></i>](#delete-posts-id-bookmark) {#delete-posts-id-bookmark .endpoint}

Delete a bookmark.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`post_id`|Post to delete a bookmark for

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/2375/bookmark" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the post a bookmark was removed from.

```json
"call for example 3"
```