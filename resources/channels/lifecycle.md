# Channel Lifecycle

Note that channels will appear "unread" if there is no stream marker for the user+channel, or if the marker's `id` is lower than the most recent message in the channel.

For details on how to use channels for private messaging, look at [How To Private Message](../../how-to/private-messages).

Endpoints:

* [Create a channel](#post-channels)
* [Update a channel](#put-channels-id)
* [Change channel owner](#put-channels-id-owner)
* [Delete a channel](#delete-channels-id)


## <span class="method method-post">POST</span> /channels {#post-channels .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Create a channel.

### POST Body Data

Name|Description
-|-
`type`|__Required__ String composed of letters, numbers, underscore, period, and dash. Up to 128 characters
`acl`|Valid ACL object. By default, everything but `type` and `user` is editable after creating the channel! Be sure to restrict editing if you want to prevent it, and read [How to ACL](../../how-to/channel-permissions)
`raw`|Embedded [raw values](/docs/implementation/raw).

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels" \
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

Update a channel. `PUT` and `PATCH` may be used.

### POST Body Data

Name|Description
-|-
`acl`|Valid ACL object. Only mutable ACLs can be updated. Full-access users and the channel creator can edit a channel, but only the creator can change who is a full-access user. Be sure to restrict editing if you want to prevent it, and read [How to ACL](../../how-to/channel-permissions)
`raw`|Embedded [raw values](/docs/implementation/raw). Not deleted unless explicitly set to empty values for each type.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/13" \
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



## <span class="method method-put">PUT</span> /channels/<span class="call-param">{channel_id}</span>/owner {#put-channels-id-owner .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">messages</span>

Change the owner of a channel.

Can not be done to `io.pnut.core.pm`-type channels.

Can only be done by the current owner of the channel. The current owner will automatically be made a `full` access user of the channel.

### POST Body Data

Name|Description
-|-
`owner_id`|User ID or `@`-username of new owner.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/13/owner" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
  \"owner_id\": \"2\"
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

Deactivate a channel. Only the creator of a channel can deactivate it. Deactivating a channel removes all subscriptions to the channel, but does nothing to the contents. It is irreversible. `io.pnut.core.pm`-type channels cannot be deactivated.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/13" \
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