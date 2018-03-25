### Post Lifecycle


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> write_post</span><span class="method method-post">POST</span> /posts [<i class="fas fa-paragraph"></i>](#post-posts) {#post-posts .endpoint}

Create a post.

On creation, you can automatically update the "personal" [stream marker](../stream-marker#post-markers) to the post's ID by including `update_marker=1` in the query string.

Posts from the same human- or feed-type user cannot contain the same `text` within 120 seconds.

`JSON` in the body of the request is also allowed. Normal links and markdown links are parsed by the server by default.

##### POST Body Data [<i class="fas fa-paragraph"></i>](#post-body-data-1) {#post-body-data-1}

Name|Description
-|-
`text`|256 character-limited string
`reply_to`|Optional ID of another post to reply to
`is_nsfw`|Optional boolean whether the post should be marked as "NSFW" (Not Safe For Work/mature/offensive)
`entities.parse_links`|Optional boolean whether the links should be parsed by the server. Default `true`
`entities.parse_markdown_links`|Optional boolean whether the markdown links should be parsed by the server. Default `true`

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -d "text=The people here are not shy." \
    -X POST \
    -H "X-Pretty-Json: 1"
```

Returns the created post.

```json
"call for example 1"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> write_post</span><span class="method method-put">PUT</span> /posts/<span class="call-param">{post_id}</span> [<i class="fas fa-paragraph"></i>](#put-posts-id) {#put-posts-id .endpoint}

Edit or "revise" a post.

* Can only be done within __300 seconds__ of the original post's creation
* Can only be done __once__ to a post
* Must contain the same [entities](../../implementation/entities) that were in the original post (Positions can change. Links can be formatted in any way, but the URLs have to be the same)

Once a revision has been made, the original post can still be retrieved from the [Revisions endpoint](lookup#get-posts-id-revisions).

Reposts made before the revision will continue to point at the original post.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`post_id`|ID of the post to revise

The POST body can be the same as when creating a post. `is_nsfw` *can* be changed from an initial post to a revision.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/2392" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -d "text=#system of a down" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the revised post.

```json
"call for example 2"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> write_post</span><span class="method method-delete">DELETE</span> /posts/<span class="call-param">{post_id}</span> [<i class="fas fa-paragraph"></i>](#delete-posts-id) {#delete-posts-id .endpoint}

Delete a post.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-2) {#url-parameters-2}

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
"call for example 3"
```