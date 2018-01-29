### Channel Lifecycle

Note that channels will appear "unread" if there is no stream marker for the user+channel, or if the marker's `id` is lower than the most recent message in the channel.

For details on how to use channels for private messaging, look at [How To Private Message](../../how-to/channels-pm).



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-post">POST</span> /channels [<i class="fas fa-paragraph"></i>](#post-channels) {#post-channels .endpoint}

Create a channel. `type` is necessary. ACLs must be valid. By default, all of it is editable after creating the channel! Be sure to restrict editing if you want to prevent it, and read [How to ACL](../../how-to/channels-acl).

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
  \"type\":\"com.example.site\",
  \"acl\":{
    \"full\": {
      \"user_ids\": [
        4,\"@wife\"
      ],
      \"immutable\":false
    },
    \"read\": {
      \"any_user\":true
    }
  }
}" \
    -X POST \
    -H "X-Pretty-Json: 1"
```

Returns the created channel

```json
"call for example 1"
```



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-put">PUT</span> /channels/<span class="call-param">{channel_id}</span> [<i class="fas fa-paragraph"></i>](#put-channels-id) {#put-channels-id .endpoint}

Update a channel. Channels are only editable if they have an ACL that is not `immutable`. Full-access users and the owner can edit a channel, but only the owner can change who is a full-access user. `PUT` and `PATCH` may be used.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/13" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
  \"acl\":{
    \"full\": {
      \"user_ids\": [
      	4
      ]
    }
  }
}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the updated channel

```json
"call for example 2"
```




#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> messages</span><span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span> [<i class="fas fa-paragraph"></i>](#delete-channels-id) {#delete-channels-id .endpoint}

Deactivate a channel. Only the owner of a channel can deactivate it. Deactivating a channel removes all subscriptions to the channel, but does nothing to the contents. It is irreversible. `io.pnut.core.pm`-type channels cannot be deactivated.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/13" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the deactivated channel

```json
"call for example 3"
```