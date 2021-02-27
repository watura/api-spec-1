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
`channel_ids`|__Required__ `pm` to search all accessible private messages, or comma-separated list of channel IDs
`client_id`|Only include messages created by this client ID
`created_after`|ISO 8601-formatted timestamp after which messages were created
`created_before`|ISO 8601-formatted timestamp before which messages were created
`creator_id`|Only include messages created by this user ID
`file_id`|Matches with this file attached
`file_kinds`|Comma-separated list of oEmbed-attached file types (`video`, `audio`, `image`, `other`)
`is_nsfw`|If false, does not include NSFW messages
`is_reply`|Whether to include messages that are or are not replies
`is_sticky`|If true, only include sticky messages
`leading_mentions`|Comma-separated list of mentions at the beginning of a message. Any matches returned
`mentions`|Comma-separated list of mentions. Any matches returned
`poll_id`|Matches with this poll attached
`raw_types`|Comma-separated list of attached raw types. Any matches returned
`reply_to`|Only include messages replying to this message
`tags`|Comma-separated list of tags. Any matches returned
`thread_id`|Only include messages in this thread
`url_domains`|Comma-separated list of domains. Any matches returned. Do not include `http://` or `www` in front of domain
`urls`|Comma-separated list of URLs. Any matches returned
`user_types`|Comma-separated list of user types of: human, feed, bot

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/messages/search?channel_ids=600,18" \
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