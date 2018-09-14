# Post Bookmarks

Bookmarking is an action for users to keep track of posts. You can see others' bookmarks as well.

Endpoints:

* [Get a user's bookmarks](#get-users-id-bookmarks)
* [Bookmark a post](#put-posts-id-bookmark)
* [Delete a bookmark](#delete-posts-id-bookmark)


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/bookmarks {#get-users-id-bookmarks .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Retrieve a list of bookmarks made by the specified user.

Returned posts may include a `note` string field if looking up bookmarks made by the authorized user.

### URL Parameters [&para;](#url-parameters) {#url-parameters}

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


## <span class="method method-put">PUT</span> /posts/<span class="call-param">{post_id}</span>/bookmark {#put-posts-id-bookmark .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">write_post</span>

Bookmark a post.

### URL Parameters [&para;](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`post_id`|Post to bookmark

### PUT Body Data [&para;](#put-body-data-1) {#put-body-data-1}

Name|Description
-|-
`note`|Optional 128-character note that will only be visible when a user retrieves their own bookmarks

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


## <span class="method method-delete">DELETE</span> /posts/<span class="call-param">{post_id}</span>/bookmark {#delete-posts-id-bookmark .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">write_post</span>

Delete a bookmark.

### URL Parameters [&para;](#url-parameters-2) {#url-parameters-2}

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