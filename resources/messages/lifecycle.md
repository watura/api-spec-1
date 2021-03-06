### Message Lifecycle




#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-post">POST</span> /channels/<span class="call-param">{channel_id}</span>/messages [<i class="fas fa-paragraph"></i>](#post-channels-id-messages) {#post-channels-id-messages .endpoint}

Create a message in a channel.

On creation, you can automatically update the stream marker to the most recent ID in the channel (marking the channel "read") by including `update_marker=1` in the query string.

For details on how to use channels for private messaging, look at [How To Private Message](../../how-to/channels-pm).

Can be `application/json` Content-Type.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the channel to create a message in.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/messages" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
    -d "text=This is a message!"
    -X POST \
    -H "X-Pretty-Json: 1"
```

Returns the message created.

```json
"call for example 1"
```



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span> [<i class="fas fa-paragraph"></i>](#delete-channels-id-messages-id) {#delete-channels-id-messages-id .endpoint}

Delete a message in a channel. Creators of messages can delete their messages even if they no longer have access to the channel.

Owners and full-access users may also delete others' messages in non-private message channels, which will also create a `deleted_by` field on those deleted messages.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`channel_id`|ID of the channel to delete a message from.
`message_id`|ID of the message to delete.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/messages/12" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the deleted message.

```json
"call for example 2"
```