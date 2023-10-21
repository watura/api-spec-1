# Post Interactions

Endpoints:

* [Get interactions made against a post](#get-posts-id-interactions)

This endpoint mirrors [User Interactions](/docs/resources/users/interactions), but for a single post, instead of a user, and it does not include `objects`.


## <span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span>/interactions {#get-posts-id-interactions .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve actions executed against a post.

### URL Parameters

Name|Description
-|-
`post_id`|ID of the post to retrieve actions for

### Query Parameters

Name|Description
-|-
`filters`|Comma-separated list of actions to filter by. Allowed: `bookmark`, `repost`, `reply`.
`exclude`|Comma-separated list of actions to exclude. `?exclude=bookmark` will return all actions except bookmarks. If `filters` is also specified, this is ignored.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/posts/83/interactions" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of interactions.

```json
{
    "meta": {
        "more": false,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {
            "pagination_id": "0",
            "event_date": "ISO 8601",
            "action": "String",
            "users": [
                {"...User Object..."}
            ]
        }
    ]
}
```
