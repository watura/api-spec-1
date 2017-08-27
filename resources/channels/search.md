### Channel Search




#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> varies</span><span class="method method-get">GET</span> /channels/search [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-channels-search) {#get-channels-search .endpoint}

Retrieve a list of channels filtered by the given criteria.

##### Query Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-parameters-1) {#query-parameters-1}

Name|Description
-|-
`order`|One of activity or id. Default is by activity
`categories`|Comma-separated list of: fun, lifestyle, profession, language, community, tech, event, general. Taken from `io.pnut.core.chat-settings` raw
`channel_types`|Comma-separated list of channel types to include
`exclude_channel_types`|Comma-separated list of channel types to exclude
`is_private`|If true, only include private channels
`is_public`|If true, only include public-readable channels
`owner_id`|Channels owned by the included user ID

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/search?is_public=1&channel_types=io.pnut.core.chat&categories=fun" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of channels

```json

```