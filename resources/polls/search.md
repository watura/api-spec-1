# Poll Search

Endpoints:

* [Search polls](#get-polls-search)


## <span class="method method-get">GET</span> /polls/search {#get-polls-search .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of polls filtered by the given criteria.

### Query Parameters

#### Sort

Name|Description
-|-
`order`|One of id or closed_at. Default is by ID

#### Filter

Name|Description
-|-
`created_after`|ISO 8601-formatted timestamp after which polls were created
`created_before`|ISO 8601-formatted timestamp before which polls were created
`creator_id`|Only include polls created by this user ID
`exclude_poll_types`|Comma-separated list of poll types to exclude
`file_id`|Matches with this file attached
`is_anonymous`|Whether to include anonymous polls
`is_closed`|Whether to include closed polls
`is_public`|Whether to include public polls
`poll_types`|Comma-separated list of poll types to include
`raw_types`|Comma-separated list of attached raw types. Any matches returned
`you_responded`|If true, only include polls you have responded to

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/polls/search?is_public=1&you_responded=0&is_closed=0" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of polls

```json
{
    "meta": {
        "more": false,
        "code": 200,
        "min_id": "0",
        "max_id": "0"
    },
    "data": [
        {"...Poll Object..."}
    ]
}
```