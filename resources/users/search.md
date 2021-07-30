# User Search

Endpoints:

* [Search users](#get-users-search)


## <span class="method method-get">GET</span> /users/search {#get-users-search .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of users filtered by the given criteria.

### Query Parameters

#### Search

Name|Description
-|-
`q`|List of words included in user profiles or names

#### Sort

Name|Description
-|-
`order`|One of id or relevance. Default is by relevance when a `q` value is set

#### Filter

Name|Description
-|-
`created_after`|ISO 8601-formatted timestamp after which users were created
`created_before`|ISO 8601-formatted timestamp before which users were created
`is_follower`|Whether to include users who follow you. Requires authentication
`is_following`|Whether to include users who you are following. Requires authentication
`locale`|[Valid user locale](../users#locales) e.g., `en_US`
`timezone`|[Valid user timezone](../users#timezones) e.g., `America/Chicago`
`user_types`|Comma-separated list of user types of: human, feed, bot

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/search?q=news&user_types=feed" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of users

```json
{
    "meta": {
        "more": false,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...User Object..."},
        {"...User Object..."}
    ]
}
```