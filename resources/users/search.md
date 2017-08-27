### User Search




#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> varies</span><span class="method method-get">GET</span> /users/search [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-search) {#get-users-search .endpoint}

Retrieve a list of users filtered by the given criteria.

##### Query Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-parameters-1) {#query-parameters-1}

Name|Description
-|-
`q`|REQUIRED List of words included in user profiles or names
`order`|One of id or relevance. Default is by relevance
`locale`|An ISO formatted locale; e.g., `en_US`
`timezone`|Timezone in tzinfo format
`types`|Comma-separated list of user types of: human, feed, bot

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/search?q=news&types=feed" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of users

```json

```