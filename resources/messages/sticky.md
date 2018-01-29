### Sticky Messages

"Sticky" messages are like bookmarks for a channel, but they are per-channel, not per-user. They will have `is_sticky: true`.

Users with `full` access to a channel are able to sticky and un-sticky messages in the channel.



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/sticky_messages [<i class="fas fa-paragraph"></i>](#get-channels-id-sticky_messages) {#get-channels-id-sticky_messages .endpoint}

Retrieve sticky messsages in a channel. The requesting user must have access to the channel.

Note that the `pagination_id` and `min_id` and `max_id` will change as users sticky and un-sticky messages.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the channel to retrieve messages from


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/sticky_messages" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of messages.

```json
"call for example 1"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-put">PUT</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span>/sticky [<i class="fas fa-paragraph"></i>](#put-channels-id-messages-id-sticky) {#put-channels-id-messages-id-sticky .endpoint}

Sticky a message.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`channel_id`|ID of the channel the message is in
`message_id`|Message to sticky


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/messages/13/sticky" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the bookmarked post.

```json
"call for example 2"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span>/sticky [<i class="fas fa-paragraph"></i>](#delete-channels-id-messages-id-sticky) {#delete-channels-id-messages-id-sticky .endpoint}

Un-sticky a message.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`channel_id`|ID of the channel the message is in
`message_id`|Message to un-sticky

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/messages/13/sticky" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the message.

```json
"call for example 3"
```