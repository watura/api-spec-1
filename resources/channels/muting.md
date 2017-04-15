### Channel Muting

Muting a channel prevents other users from being able to auto-subscribe you to that channel.



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-get">GET</span> /users/me/channels/muted [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-me-channels-muted) {#get-users-me-channels-muted .endpoint}

Retrieve a list of channels the authenticated user has muted.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels/muted" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of muted channels.

```json
{
  "meta": {
    "more": false,
    "min_id": "4",
    "max_id": "4",
    "code": 200
  },
  "data": [
    {
      "id": "2",
      "type": "com.example.site",
      "owner": {...},
      "recent_message_id": "6",
      "acl": {
        "full": {
          "immutable": true,
          "you": false,
          "user_ids": []
        },
        "write": {
          "any_user": false,
          "immutable": true,
          "you": false,
          "user_ids": []
        },
        "read": {
          "any_user": true,
          "immutable": true,
          "public": false,
          "you": true,
          "user_ids": []
        }
      },
      "counts": {
        "messages": 6
      },
      "you_subscribed": false,
      "you_muted": true,
      "has_unread": true,
      "pagination_id": "4"
    }
  ]
}
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-put">PUT</span> /channels/<span class="call-param">{channel_id}</span>/mute [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-channels-id-mute) {#put-channels-id-mute .endpoint}

Mute subscriptions for a channel. Muting unsubscribes, if you were subscribed.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the channel to mute.


##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/2/mute" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT
```

Returns the muted channel.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "2",
    "type": "com.example.site",
    "owner": {...},
    "recent_message_id": "6",
    "acl": {
      "full": {
        "immutable": true,
        "you": false,
        "user_ids": []
      },
      "write": {
        "any_user": false,
        "immutable": true,
        "you": false,
        "user_ids": []
      },
      "read": {
        "any_user": true,
        "immutable": true,
        "public": false,
        "you": true,
        "user_ids": []
      }
    },
    "counts": {
      "messages": 6
    },
    "you_subscribed": false,
    "you_muted": true,
    "has_unread": true
  }
}
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span>/mute [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-channels-id-mute) {#delete-channels-id-mute .endpoint}

Delete a subscription mute for a channel.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`channel_id`|ID of the channel to unmute.


##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/4/mute" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE
```

Returns the unmuted channel.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "2",
    "type": "com.example.site",
    "owner": {...},
    "recent_message_id": "6",
    "acl": {
      "full": {
        "immutable": true,
        "you": false,
        "user_ids": []
      },
      "write": {
        "any_user": false,
        "immutable": true,
        "you": false,
        "user_ids": []
      },
      "read": {
        "any_user": true,
        "immutable": true,
        "public": false,
        "you": true,
        "user_ids": []
      }
    },
    "counts": {
      "messages": 6
    },
    "you_subscribed": false,
    "you_muted": false,
    "has_unread": true
  }
}
```