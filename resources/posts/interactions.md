# Post Interactions

Bookmarks, Replies, and Reposts.

Endpoints:

* [Get interactions made against a post](#get-posts-id-interactions)


## <span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span>/interactions {#get-posts-id-interactions .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve actions executed against a post.

### URL Parameters [&para;](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`post_id`|ID of the post to retrieve actions for

### Query Parameters [&para;](#query-parameters-1) {#query-parameters-1}

Name|Description
-|-
`filters`|Comma-separated list of actions to filter by. Allowed: `bookmark`, `repost`, `reply`.
`exclude`|Comma-separated list of actions to exclude. `?exclude=bookmark` will return all actions except bookmarks. If `filters` is also specified, this is ignored.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/83/interactions" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of interactions.

```json
"call for example 1"
```