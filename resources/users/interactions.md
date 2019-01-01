# User Interactions

Users may see some common actions that have been made against their self, posts, polls, etcetera. Events from multiple users are grouped into the most recent event of the same type and object, within a short time.

*E.g.*, if two users repost the same post of yours within a day, they may be included in a single event. But further apart, they would be included as separate events.

### Objects by Action

Action|Objects
-|-
`bookmark`, `reply`, `repost`|Post
`follow`|User
`poll_response`|Poll

The poll included from a `poll_response` action is static and abbreviated like that included embedded in `io.pnut.core.poll` raw. If the poll is anonymous, `users` will not be included.

Endpoints:

* [Get user interactions](#get-users-me-interactions)


## <span class="method method-get">GET</span> /users/me/interactions {#get-users-me-interactions .endpoint}

Scope: <span class="endpoint-meta">any</span>

Retrieve actions executed against the authenticated user and their content.

### Query Parameters

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
{
    "meta": {
        "more": true,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {
            "pagination_id": "0",
            "event_date": "ISO 8601",
            "action": "String",
            "objects": [
                {"...Post Object..."}
            ],
            "users": [
                {"...User Object..."},
                {"...User Object..."}
            ]
        }
    ]
}
```