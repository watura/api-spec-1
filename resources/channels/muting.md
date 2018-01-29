### Channel Muting

Muting a channel prevents other users from being able to auto-subscribe you to that channel.



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-get">GET</span> /users/me/channels/muted [<i class="fas fa-paragraph"></i>](#get-users-me-channels-muted) {#get-users-me-channels-muted .endpoint}

Retrieve a list of channels the authenticated user has muted.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels/muted" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of muted channels.

```json
"call for example 1"
```



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-put">PUT</span> /channels/<span class="call-param">{channel_id}</span>/mute [<i class="fas fa-paragraph"></i>](#put-channels-id-mute) {#put-channels-id-mute .endpoint}

Mute subscriptions for a channel. Muting unsubscribes, if you were subscribed.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the channel to mute.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/2/mute" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the muted channel.

```json
"call for example 2"
```



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span>/mute [<i class="fas fa-paragraph"></i>](#delete-channels-id-mute) {#delete-channels-id-mute .endpoint}

Delete a subscription mute for a channel.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`channel_id`|ID of the channel to unmute.


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/4/mute" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the unmuted channel.

```json
"call for example 3"
```