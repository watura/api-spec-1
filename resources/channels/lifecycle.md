### Channel Lifecycle

Note that channels will appear "unread" if there is no stream marker for the user+channel, or if the marker's `id` is lower than the most recent message in the channel.

For details on how to use channels for private messaging, look at [How To Private Message](../../how-to/channels-pm).



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> varies</span><span class="method method-post">POST</span> /channels [<i class="fa fa-paragraph" aria-hidden="true"></i>](#post-channels) {#post-channels .endpoint}

Create a channel. `type` is necessary. ACLs must be valid. By default, all of it is editable after creating the channel! Be sure to restrict editing if you want to prevent it, and read [How to ACL](../../how-to/channels-acl).

##### Example Call {.example-code}

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
    -X POST
```

Returns the created channel

```json
{
  "meta": {
    "code": 201
  },
  "data": {
    "id": "13",
    "type": "com.example.site",
    "owner": {
      "id": "1",
      "created_at": "2016-09-08T17:16:39Z",
      "guid": "113BA773-F1F2-42CF-99F8-02EC778942C9",
      "locale": "en_US",
      "timezone": "America/Chicago",
      "type": "human",
      "username": "33MHz",
      "name": "Robert",
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"6\" data-mention-name=\"pnut\" itemprop=\"mention\">@pnut</span> developer. Coder by day, coder by night.</span>",
        "text": "@pnut developer. Coder by day, coder by night.",
        "entities": {
          "links": [],
          "mentions": [
            {
              "id": "6",
              "len": 5,
              "pos": 0,
              "text": "pnut",
              "is_leading": true
            }
          ],
          "tags": []
        },
        "avatar_image": {
          "height": 1200,
          "width": 1200,
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/4hxiGBxrSHhBzcABGX45sJxcFsHEJ_1Kq2o04iZ2-siG--l1CONPCNRvzhwW1HWXQ3DqNxyvzj4LlY1x9EJ_Or1xGGqM9iAQxFnV1lIOx6hVnq6Tm6oX714IGgovER3dYC98oLsoj7ND",
          "is_default": false
        },
        "cover_image": {
          "height": 400,
          "width": 1024,
          "link": "https://d26y28lt6cxszo.cloudfront.net/cover/2f8b4364838cc35ea5461332cca072be1126ccbf47106353908ffbe6a994922c8086f31fff1d619d334db30240e7be474cde33e8598c172ec3d8826baf325c70d3fe897feb33",
          "is_default": false
        }
      },
      "counts": {
        "bookmarks": 7,
        "clients": 4,
        "followers": 69,
        "following": 66,
        "posts": 890,
        "users": 70
      },
      "verified": {
        "domain": "codespelunkers.com",
        "link": "http://codespelunkers.com"
      },
      "follows_you": true,
      "you_blocked": false,
      "you_follow": true,
      "you_muted": false,
      "you_can_follow": false
    },
    "acl": {
      "full": {
        "immutable": false,
        "you": true,
        "user_ids": [
          "2",
          "4"
        ]
      },
      "write": {
        "any_user": false,
        "immutable": true,
        "you": true,
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
      "messages": 0,
      "subscribers": 3
    },
    "you_subscribed": true,
    "you_muted": false,
    "has_unread": false
  }
}
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> varies</span><span class="method method-put">PUT</span> /channels/<span class="call-param">{channel_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-channels-id) {#put-channels-id .endpoint}

Update a channel. Channels are only editable if they have an ACL that is not `immutable`. Full-access users and the owner can edit a channel, but only the owner can change who is a full-access user. `PUT` and `PATCH` may be used.

##### Example Call {.example-code}

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
    -X PUT
```

Returns the updated channel

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "13",
    "type": "com.example.site",
    "owner": {
      "id": "1",
      "created_at": "2016-09-09T17:16:39Z",
      "guid": "113BA773-F1F2-42CF-99F8-02EC778942C9",
      "locale": "en_US",
      "timezone": "America/Chicago",
      "type": "human",
      "username": "33MHz",
      "name": "Robert",
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"6\" data-mention-name=\"pnut\" itemprop=\"mention\">@pnut</span> developer. Coder by day, coder by night.</span>",
        "text": "@pnut developer. Coder by day, coder by night.",
        "entities": {
          "links": [],
          "mentions": [
            {
              "id": "6",
              "len": 5,
              "pos": 0,
              "text": "pnut",
              "is_leading": true
            }
          ],
          "tags": []
        },
        "avatar_image": {
          "height": 1200,
          "width": 1200,
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/4hxiGBxrSHhBzcABGX45sJxcFsHEJ_1Kq2o04iZ2-siG--l1CONPCNRvzhwW1HWXQ3DqNxyvzj4LlY1x9EJ_Or1xGGqM9iAQxFnV1lIOx6hVnq6Tm6oX714IGgovER3dYC98oLsoj7ND",
          "is_default": false
        },
        "cover_image": {
          "height": 400,
          "width": 1024,
          "link": "https://d26y28lt6cxszo.cloudfront.net/cover/2f8b4364838cc35ea5461332cca072be1126ccbf47106353908ffbe6a994922c8086f31fff1d619d334db30240e7be474cde33e8598c172ec3d8826baf325c70d3fe897feb33",
          "is_default": false
        }
      },
      "counts": {
        "bookmarks": 7,
        "clients": 4,
        "followers": 69,
        "following": 66,
        "posts": 890,
        "users": 70
      },
      "verified": {
        "domain": "codespelunkers.com",
        "link": "http://codespelunkers.com"
      },
      "follows_you": true,
      "you_blocked": false,
      "you_follow": true,
      "you_muted": false,
      "you_can_follow": false
    },
    "acl": {
      "full": {
        "immutable": false,
        "you": true,
        "user_ids": [
          "4"
        ]
      },
      "write": {
        "any_user": false,
        "immutable": true,
        "you": true,
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
      "messages": 0,
      "subscribers": 2
    },
    "you_subscribed": true,
    "you_muted": false,
    "has_unread": false
  }
}
```




#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> varies</span><span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-channels-id) {#delete-channels-id .endpoint}

Deactivate a channel. Only the owner of a channel can deactivate it. Deactivating a channel removes all subscriptions to the channel, but does nothing to the contents. It is irreversible. `io.pnut.core.pm`-type channels cannot be deactivated.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/13" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE
```

Returns the deactivated channel

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "13",
    "type": "com.example.site",
    "owner": {
      "id": "1",
      "created_at": "2016-09-09T17:16:39Z",
      "guid": "113BA773-F1F2-42CF-99F8-02EC778942C9",
      "locale": "en_US",
      "timezone": "America/Chicago",
      "type": "human",
      "username": "33MHz",
      "name": "Robert",
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"6\" data-mention-name=\"pnut\" itemprop=\"mention\">@pnut</span> developer. Coder by day, coder by night.</span>",
        "text": "@pnut developer. Coder by day, coder by night.",
        "entities": {
          "links": [],
          "mentions": [
            {
              "id": "6",
              "len": 5,
              "pos": 0,
              "text": "pnut",
              "is_leading": true
            }
          ],
          "tags": []
        },
        "avatar_image": {
          "height": 1200,
          "width": 1200,
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/4hxiGBxrSHhBzcABGX45sJxcFsHEJ_1Kq2o04iZ2-siG--l1CONPCNRvzhwW1HWXQ3DqNxyvzj4LlY1x9EJ_Or1xGGqM9iAQxFnV1lIOx6hVnq6Tm6oX714IGgovER3dYC98oLsoj7ND",
          "is_default": false
        },
        "cover_image": {
          "height": 400,
          "width": 1024,
          "link": "https://d26y28lt6cxszo.cloudfront.net/cover/2f8b4364838cc35ea5461332cca072be1126ccbf47106353908ffbe6a994922c8086f31fff1d619d334db30240e7be474cde33e8598c172ec3d8826baf325c70d3fe897feb33",
          "is_default": false
        }
      },
      "counts": {
        "bookmarks": 7,
        "clients": 4,
        "followers": 69,
        "following": 66,
        "posts": 890,
        "users": 70
      },
      "verified": {
        "domain": "codespelunkers.com",
        "link": "http://codespelunkers.com"
      },
      "follows_you": true,
      "you_blocked": false,
      "you_follow": true,
      "you_muted": false,
      "you_can_follow": false
    },
    "acl": {
      "full": {
        "immutable": false,
        "you": true,
        "user_ids": [
          "4"
        ]
      },
      "write": {
        "any_user": false,
        "immutable": true,
        "you": true,
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
      "messages": 0,
      "subscribers": 0
    },
    "you_subscribed": false,
    "you_muted": false,
    "has_unread": false,
    "is_active": false
  }
}
```