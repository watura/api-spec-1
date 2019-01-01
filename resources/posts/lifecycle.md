# Post Lifecycle

Endpoints:

* [Create a post](#post-posts)
* [Revise a post](#put-posts-id)
* [Delete a post](#delete-posts-id)


## <span class="method method-post">POST</span> /posts {#post-posts .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">write_post</span>

Create a post.

On creation, you can automatically update the "personal" [stream marker](../stream-marker#post-markers) to the post's ID by including `update_marker=1` in the query string.

Posts from the same human- or feed-type user cannot contain the same `text` within 120 seconds.

An `application/json` Content-Type is preferred over form. Normal links and markdown links are parsed by the server by default.

### POST Body Data

Name|Description
-|-
`text`|__Required__ 256 character-limited string
`reply_to`|ID of another post to reply to
`is_nsfw`|Boolean whether the post should be marked as "NSFW" (Not Safe For Work/mature/offensive). Including the tag `#nsfw` in the post body will mark a post NSFW unless overridden by this.
`entities.parse_links`|Boolean whether the links should be parsed by the server. Default `true`
`entities.parse_markdown_links`|Boolean whether the markdown links should be parsed by the server. Default `true`

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{\"text\": \"The people here are not shy.\"}" \
    -X POST \
    -H "X-Pretty-Json: 1"
```

Returns the created post.

```json
{
    "meta": {
        "code": 201
    },
    "data": {"...Post Object..."}
}
```


## <span class="method method-put">PUT</span> /posts/<span class="call-param">{post_id}</span> {#put-posts-id .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">write_post</span>

Edit or "revise" a post.

* Can only be done within __300 seconds__ of the original post's creation
* Can only be done __once__ to a post
* Must contain the same [entities](../../implementation/entities) that were in the original post (Positions can change. Links can be formatted in any way, but the URLs have to be the same)

Once a revision has been made, the original post can still be retrieved from the [Revisions endpoint](lookup#get-posts-id-revisions).

Reposts made before the revision will continue to point at the original post.

### URL Parameters

Name|Description
-|-
`post_id`|ID of the post to revise

The POST body can be the same as when creating a post. `is_nsfw` *can* be changed from an initial post to a revision.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/2392" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{\"text\": \"system of a down\"}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the revised post.

```json
{
    "meta": {
        "code": 201
    },
    "data": {"...Post Object..."}
}
```


## <span class="method method-delete">DELETE</span> /posts/<span class="call-param">{post_id}</span> {#delete-posts-id .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">write_post</span>

Delete a post.

### URL Parameters

Name|Description
-|-
`post_id`|ID of the post to delete

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/2392" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the deleted post.

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...Post Object..."}
}
```