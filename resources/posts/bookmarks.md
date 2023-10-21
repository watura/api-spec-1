# Post Bookmarks

Endpoints:

* [Get a user's bookmarks](#get-users-id-bookmarks)
* [Bookmark a post](#put-posts-id-bookmark)
* [Delete a bookmark](#delete-posts-id-bookmark)

Bookmarking is an action for users to keep track of posts. You can see others' bookmarks as well.


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/bookmarks {#get-users-id-bookmarks .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Retrieve a list of bookmarks made by the specified user.

Returned posts may include a `note` string field if looking up bookmarks made by the authorized user.

### URL Parameters

Name|Description
-|-
`user_id`|What user's bookmarks to look up

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/1/bookmarks" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts.

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


## <span class="method method-put">PUT</span> /posts/<span class="call-param">{post_id}</span>/bookmark {#put-posts-id-bookmark .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">write_post</span>

Bookmark a post.

### URL Parameters

Name|Description
-|-
`post_id`|Post to bookmark

### PUT Body Data

Name|Description
-|-
`note`|Optional 128-character note that will only be visible when a user retrieves their own bookmarks. It is not escaped.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/posts/2375/bookmark" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{\"note\": \"Robert has great posts.\"}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the bookmarked post.

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...Post Object..."}
}
```


## <span class="method method-delete">DELETE</span> /posts/<span class="call-param">{post_id}</span>/bookmark {#delete-posts-id-bookmark .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">write_post</span>

Delete a bookmark.

### URL Parameters

Name|Description
-|-
`post_id`|Post to delete a bookmark for

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/posts/2375/bookmark" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the post a bookmark was removed from.

```json
{
    "meta": {
        "code": 200
    },
    "data": {"....Post Object..."}
}
```
