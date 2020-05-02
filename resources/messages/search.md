# Message Search

Endpoints:

* [Search messages](#get-channels-messages-search)


## <span class="method method-get">GET</span> /channels/messages/search {#get-channels-messages-search .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of messages filtered by the given criteria.

### Query Parameters

#### Search

Name|Description
-|-
`q`|List of words included in messages

#### Sort

Name|Description
-|-
`order`|One of id or relevance. Default is by relevance

#### Filter

Name|Description
-|-
`channel_ids`|REQUIRED "pm" to search all accessible private messages, or comma-separated list of channel IDs
`tags`|Comma-separated list of tags. Any matches returned. Do not include `#`
`mentions`|Comma-separated list of mentions. Any matches returned. Do not include `@`
`leading_mentions`|Comma-separated list of mentions at the beginning of a message. Any matches returned. Do not include `@`
`links`|Comma-separated list of URLs. Any matches returned
`link_domains`|Comma-separated list of domains. Any matches returned. Do not include `http://` or `www` in front of domain
`is_nsfw`|If false, does not include NSFW messages
`is_reply`|If set, only include messages that are or are not replies
`is_sticky`|If true, only include sticky messages
`client_id`|Only include messages created by this client ID
`creator_id`|Only include messages created by this user ID
`reply_to`|Only include messages replying to this message
`thread_id`|Only include messages in this thread
`user_types`|Comma-separated list of user types of: human, feed, bot
`raw_types`|Comma-separated list of attached raw types. Any matches returned

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/messages/search?channel_ids=600,18" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of messages

```json
{
    "meta": {
        "more": false,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...Message Object..."}
    ]
}
```