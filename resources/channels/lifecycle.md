# Channel Lifecycle

Note that channels will appear "unread" if there is no stream marker for the user+channel, or if the marker's `id` is lower than the most recent message in the channel.

For details on how to use channels for private messaging, look at [How To Private Message](../../how-to/channels-pm).

Endpoints:

* [Create a channel](#post-channels)
* [Update a channel](#put-channels-id)
* [Delete a channel](#delete-channels-id)


## <span class="method method-post">POST</span> /channels {#post-channels .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

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
{
    "meta": {
        "code": 201
    },
    "data": {"...Channel Object..."}
}
```



## <span class="method method-put">PUT</span> /channels/<span class="call-param">{channel_id}</span> {#put-channels-id .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

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
{
    "meta": {
        "code": 200
    },
    "data": {"...Channel Object..."}
}
```




## <span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span> {#delete-channels-id .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

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
{
    "meta": {
        "code": 200
    },
    "data": {"....Channel Object..."}
}
```