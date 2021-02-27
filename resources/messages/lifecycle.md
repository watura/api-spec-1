# Message Lifecycle

Endpoints:

* [Create a message](#post-channels-id-messages)
* [Delete a message](#delete-channels-id-messages-id)


## <span class="method method-post">POST</span> /channels/<span class="call-param">{channel_id}</span>/messages {#post-channels-id-messages .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Create a message in a channel.

On creation, you can automatically update the stream marker to the most recent ID in the channel (marking the channel "read") by including `update_marker=1` in the query string.

For details on how to use channels for private messaging, look at [How To Private Message](../../how-to/private-messages).

Must be `application/json` Content-Type.

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the channel to create a message in.

### POST Body Data

Name|Description
-|-
`text`|__Required__ 2048 character-limited string
`reply_to`|ID of another message to reply to
`is_nsfw`|Boolean whether the message should be marked as "NSFW" (Not Safe For Work/mature/offensive). Including the tag `#nsfw` in the message body will mark a message NSFW unless overridden by this.
`entities.parse_links`|Boolean whether the links should be parsed by the server. Default `true`
`entities.parse_markdown_links`|Boolean whether the markdown links should be parsed by the server. Default `true`
`raw`|Embedded [raw values](/docs/implementation/raw).

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/5/messages" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{\"text\": \"This is a message!\"}" \
    -X POST \
    -H "X-Pretty-Json: 1"
```

Returns the message created.

```json
{
    "meta": {
        "code": 201
    },
    "data": {"...Message Object..."}
}
```



## <span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span> {#delete-channels-id-messages-id .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Delete a message in a channel. Creators of messages can delete their messages even if they no longer have access to the channel.

Channel creators and full-access users may also delete others' messages in non-private message channels, which will also create a `deleted_by` field on those deleted messages.

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the channel to delete a message from.
`message_id`|ID of the message to delete.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/5/messages/12" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the deleted message.

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...Message Object..."}
}
```