# User Interactions

Bookmarks, Replies, Reposts, Follows, and Poll responses.

Endpoints:

* [Get user interactions](#get-users-me-interactions)


## <span class="method method-get">GET</span> /users/me/interactions {#get-users-me-interactions .endpoint}

Scope: <span class="endpoint-meta">any</span>

Retrieve actions executed against the authenticated user and their posts.

### Query Parameters [&para;](#query-parameters-2) {#query-parameters-2}

Name|Description
-|-
`filters`|Comma-separated list of actions to filter by. `?filters=bookmark` will only include bookmarks. Allowed: `bookmark`, `repost`, `reply`, `follow`, `poll_response`.
`exclude`|Comma-separated list of actions to exclude. `?exclude=bookmark` will return all actions except bookmarks. If `filters` is also specified, this is ignored.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/interactions" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of interactions.

```json
"call for example 2"
```