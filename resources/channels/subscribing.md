### Channel Subscribing

Subscribed channels act like an "inbox" of channels ordered by their most recent messages.



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-get">GET</span> /users/me/channels/subscribed [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-me-channels-subscribed) {#get-users-me-channels-subscribed .endpoint}

Retrieve a list of channels the authenticated user is subscribed to.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels/subscribed" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of subscribed channels.

```json
{
  "meta": {
    "more": false,
    "max_id": "5",
    "min_id": "1",
    "unread_counts": {
      "io.pnut.core.pm": 1
    },
    "code": 200
  },
  "data": [
    {
      "id": "5",
      "type": "io.pnut.33mhz",
      "owner": {...},
      "recent_message_id": "12",
      "acl": {
        "full": {
          "immutable": true,
          "you": true,
          "user_ids": []
        },
        "write": {
          "any_user": true,
          "immutable": false,
          "you": true,
          "user_ids": []
        },
        "read": {
          "any_user": true,
          "immutable": false,
          "public": false,
          "you": true,
          "user_ids": []
        }
      },
      "counts": {
        "messages": 1,
        "subscribers": 1
      },
      "you_subscribed": true,
      "you_muted": false,
      "has_unread": true,
      "pagination_id": "5"
    },
    {
      "id": "10",
      "type": "io.pnut.core.pm",
      "owner": {...},
      "recent_message_id": "10",
      "acl": {
        "full": {
          "immutable": true,
          "you": true,
          "user_ids": []
        },
        "write": {
          "any_user": false,
          "immutable": true,
          "you": true,
          "user_ids": [
            "2"
          ]
        },
        "read": {
          "any_user": false,
          "immutable": true,
          "public": false,
          "you": true,
          "user_ids": []
        }
      },
      "counts": {
        "messages": 1,
        "subscribers": 2
      },
      "you_subscribed": true,
      "you_muted": false,
      "has_unread": true,
      "pagination_id": "4"
    },
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
      "you_subscribed": true,
      "you_muted": false,
      "has_unread": true,
      "pagination_id": "3"
    },
    {
      "id": "12",
      "type": "com.example.site",
      "owner": {...},
      "acl": {
        "full": {
          "immutable": true,
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
      "has_unread": false,
      "pagination_id": "2"
    },
    {
      "id": "11",
      "type": "com.example.site",
      "owner": {...},
      "acl": {
        "full": {
          "immutable": true,
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
      "has_unread": false,
      "pagination_id": "1"
    }
  ]
}
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/subscribers [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-channels-id-subscribers) {#get-channels-id-subscribers .endpoint}

Retrieve a list of users subscribed to a channel.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the channel retrieve subscribers for.


##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/15/subscribers" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of users.

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {
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
        "bookmarks": 20,
        "clients": 4,
        "followers": 92,
        "following": 91,
        "posts": 1404,
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
    {
      "id": "20",
      "created_at": "2016-09-12T06:53:05Z",
      "guid": "978916B1-8F6D-4282-A219-53E828B60AD5",
      "locale": "en_US",
      "timezone": "Europe/Paris",
      "type": "human",
      "username": "ericd",
      "name": "Eric D.",
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Sound engineer by day, coder by night.</span>",
        "text": "Sound engineer by day, coder by night.",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        },
        "avatar_image": {
          "height": 1071,
          "width": 1071,
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/p_GqeLflIgVHIG1X7XnMZMDl84ZlH6q_2bIi3X3nHhOanA3AGeSV5NISiLGVl4R4uIC6PqGDPGIZalzmhLAQLk-hQMGHqu8G-lQysiSm8e7DNXTEnZZhcN3YcYgpn9_dp-3_DuUSHZ-2",
          "is_default": false
        },
        "cover_image": {
          "height": 1010,
          "width": 2115,
          "link": "https://d26y28lt6cxszo.cloudfront.net/cover/KXa-L5dlCkotqEpMnKG1jy-iBH8Xxo_S1nwBoSEx6PBIEPGLtlTGDKJm1NIdWAB-ZMkQ-4Z61iTV76EQhIv-MGZ3SqLMrYs7gZM6zWRL6UcMXQ02iqN-ieoA2_i71wIUPMpvtC-0JjXD",
          "is_default": false
        }
      },
      "counts": {
        "bookmarks": 22,
        "clients": 1,
        "followers": 25,
        "following": 71,
        "posts": 257,
        "users": 1
      },
      "follows_you": true,
      "you_blocked": false,
      "you_follow": true,
      "you_muted": false,
      "you_can_follow": true
    }
  ]
}
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-put">PUT</span> /channels/<span class="call-param">{channel_id}</span>/subscribe [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-channels-id-subscribe) {#put-channels-id-subscribe .endpoint}

Subscribe to updates from a channel. Subscribing unmutes it, if you were muting it.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`channel_id`|ID of the channel to subscribe to.


##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/subscribe" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT
```

Returns the subscribed channel.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "5",
    "type": "io.pnut.33mhz",
    "owner": {...},
    "recent_message_id": "12",
    "acl": {
      "full": {
        "immutable": true,
        "you": true,
        "user_ids": []
      },
      "write": {
        "any_user": true,
        "immutable": false,
        "you": true,
        "user_ids": []
      },
      "read": {
        "any_user": true,
        "immutable": false,
        "public": false,
        "you": true,
        "user_ids": []
      }
    },
    "counts": {
      "messages": 1,
      "subscribers": 1
    },
    "you_subscribed": true,
    "you_muted": false,
    "has_unread": true
  }
}
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span>/subscribe [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-channels-id-subscribe) {#delete-channels-id-subscribe .endpoint}

Delete a subscription for a channel. Unsubscribing also deletes any existing stream marker for the channel.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`channel_id`|ID of the channel to unsubscribe from.


##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/subscribe" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE
```

Returns the unsubscribed channel.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "5",
    "type": "io.pnut.33mhz",
    "owner": {...},
    "recent_message_id": "12",
    "acl": {
      "full": {
        "immutable": true,
        "you": true,
        "user_ids": []
      },
      "write": {
        "any_user": true,
        "immutable": false,
        "you": true,
        "user_ids": []
      },
      "read": {
        "any_user": true,
        "immutable": false,
        "public": false,
        "you": true,
        "user_ids": []
      }
    },
    "counts": {
      "messages": 1,
      "subscribers": 0
    },
    "you_subscribed": false,
    "you_muted": false,
    "has_unread": true
  }
}
```