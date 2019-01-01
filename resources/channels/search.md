# Channel Search

Endpoints:

* [Search channels](#get-channels-search)


## <span class="method method-get">GET</span> /channels/search {#get-channels-search .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of channels filtered by the given criteria.

### Query Parameters

#### Sort

Name|Description
-|-
`order`|One of activity or id. Default is by activity

#### Filter

Name|Description
-|-
`categories`|Comma-separated list of: fun, lifestyle, profession, language, community, tech, event, general. Taken from `io.pnut.core.chat-settings` raw
`channel_types`|Comma-separated list of channel types to include
`raw_types`|Comma-separated list of attached raw types. Any matches returned
`exclude_channel_types`|Comma-separated list of channel types to exclude
`is_private`|If true, only include private channels
`is_public`|If true, only include public-readable channels
`owner_id`|Channels owned by the included user ID

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/search?is_public=1&channel_types=io.pnut.core.chat&categories=fun" \
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