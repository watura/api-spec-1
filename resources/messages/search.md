### Message Search




#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> varies</span><span class="method method-get">GET</span> /channels/messages/search [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-channels-messages-search) {#get-channels-messages-search .endpoint}

Retrieve a list of messages filtered by the given criteria.

##### Query Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-parameters-1) {#query-parameters-1}

Name|Description
-|-
`channel_ids`|REQUIRED "pm" to search all accessible private messages, or comma-separated list of channel IDs
`order`|One of id or relevance. Default is by relevance
`q`|List of words included in messages
`tags`|Comma-separated list of tags. Any matches returned. Do not include `#`
`mentions`|Comma-separated list of mentions. Any matches returned. Do not include `@`
`leading_mentions`|Comma-separated list of mentions at the beginning of a message. Any matches returned. Do not include `@`
`links`|Comma-separated list of URLs. Any matches returned
`link_domains`|Comma-separated list of domains. Any matches returned. Do not include `http://` or `www` in front of domain
`is_nsfw`|If false, does not include NSFW messages
`is_reply`|If true, only include replies
`is_sticky`|If true, only include sticky messages
`client_id`|Only include messages created by this client ID
`creator_id`|Only include messages created by this user ID
`reply_to`|Only include messages replying to this message
`thread_id`|Only include messages in this thread
`user_types`|Comma-separated list of user types of: human, feed, bot

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/messages/search?channel_ids=600,18" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of messages

```json

```