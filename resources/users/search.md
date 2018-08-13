# User Search




## <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /users/search [&para;](#get-users-search) {#get-users-search .endpoint}

Retrieve a list of users filtered by the given criteria.

### Query Parameters [&para;](#query-parameters-1) {#query-parameters-1}

Name|Description
-|-
`q`|REQUIRED List of words included in user profiles or names
`order`|One of id or relevance. Default is by relevance
`locale`|An ISO formatted locale; e.g., `en_US`
`timezone`|Timezone in tzinfo format
`types`|Comma-separated list of user types of: human, feed, bot

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/search?q=news&types=feed" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of users

```json
"call for example 1"
```