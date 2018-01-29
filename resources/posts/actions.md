### Post Actions

Bookmarks, Replies, Reposts, and Follows.


#### <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span>/actions [<i class="fas fa-paragraph"></i>](#get-posts-id-actions) {#get-posts-id-actions .endpoint}

Retrieve actions executed against a post.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`post_id`|ID of the post to retrieve actions for

##### Query Parameters [<i class="fas fa-paragraph"></i>](#query-parameters-1) {#query-parameters-1}

Name|Description
-|-
`filters`|Comma-separated list of actions to filter by. Allowed: bookmark, repost, reply, follow.
`exclude`|Comma-separated list of actions to exclude. `?exclude=bookmark` will return all actions except bookmarks. If `filters` is also specified, this is ignored.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/83/actions" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of actions.

```json
"call for example 1"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> any</span><span class="method method-get">GET</span> /users/me/actions [<i class="fas fa-paragraph"></i>](#get-users-me-actions) {#get-users-me-actions .endpoint}

Retrieve actions executed against the authenticated user and their posts.

##### Query Parameters [<i class="fas fa-paragraph"></i>](#query-parameters-2) {#query-parameters-2}

Name|Description
-|-
`filters`|Comma-separated list of actions to filter by. `?filters=bookmark` will only include bookmarks.
`exclude`|Comma-separated list of actions to exclude. `?exclude=bookmark` will return all actions except bookmarks. If `filters` is also specified, this is ignored.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/actions" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of actions.

```json
"call for example 2"
```