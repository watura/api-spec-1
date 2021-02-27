# Channel Search

Endpoints:

* [Search channels](#get-channels-search)


## <span class="method method-get">GET</span> /channels/search {#get-channels-search .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of channels filtered by the given criteria.

### Query Parameters

#### Search

Name|Description
-|-
`q`|Basic text string searched for in `name`s and `description`s in a channel's `io.pnut.core.chat-settings` raw.

#### Sort

Name|Description
-|-
`order`|One of activity (most recent message), id (most recently created), or popularity (how many messages have been made). Default is by activity.

#### Filter

Name|Description
-|-
`categories`|Comma-separated list of: fun, lifestyle, profession, language, community, tech, event, general. Taken from `io.pnut.core.chat-settings` raw
`channel_types`|Comma-separated list of channel types to include
`created_after`|ISO 8601-formatted timestamp after which channels were created
`created_before`|ISO 8601-formatted timestamp before which channels were created
`owner_id`|Channels owned by the included user ID
`exclude_channel_types`|Comma-separated list of channel types to exclude
`file_id`|Matches with this file attached
`is_public`|Whether to include public-readable channels
`raw_types`|Comma-separated list of attached raw types. Any matches returned

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/search?is_public=1&channel_types=io.pnut.core.chat&categories=fun" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of channels

```json
{
    "meta": {
        "more": false,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...Channel Object..."}
    ]
}
```