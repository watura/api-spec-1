### Channel Lookup

To only retrieve channels by certain types, include them in a comma-separated list in the query parameter like so: `channel_types=io.pnut.core.pm,com.example.site`.



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> varies</span><span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-channels-id) {#get-channels-id .endpoint}

Retrieve a channel object.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the requested channel

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns the requested channel

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


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> varies</span><span class="method method-get">GET</span> /channels [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-channels) {#get-channels .endpoint}

Retrieve a list of specified channel objects. Only returns the first 200 found.

##### Query String Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-string-parameters) {#query-string-parameters}

Name|Description
-|-
`ids`|Comma-separated list of channel IDs

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels?ids=3,4,16" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of channels

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {
      "id": "3",
      "type": "com.example.site",
      "is_active": false,
      "owner": {...},
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
      "you_muted": true,
      "has_unread": false
    },
    {
      "id": "4",
      "type": "com.example.site",
      "is_active": false,
      "owner": {...},
      "acl": {
        "full": {
          "immutable": true,
          "you": true,
          "user_ids": [
            "2",
            "9"
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
      "you_muted": true,
      "has_unread": false
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-get">GET</span> /users/me/channels [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-me-channels) {#get-users-me-channels .endpoint}

Retrieve a list of channels created by the authenticated user.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of channels

```json
{
  "meta": {
    "more": false,
    "min_id": "5",
    "max_id": "12",
    "code": 200
  },
  "data": [
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
      "pagination_id": "12"
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
      "pagination_id": "11"
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
      "pagination_id": "10"
    },
    {
      "id": "6",
      "type": "io.pnut.core.pm",
      "owner": {...},
      "recent_message_id": "7",
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
          "user_ids": []
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
        "subscribers": 0
      },
      "you_subscribed": false,
      "you_muted": false,
      "has_unread": true,
      "pagination_id": "6"
    },
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
    }
  ]
}
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-get">GET</span> /users/me/channels/existing_pm [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-me-channels-existing_pm) {#get-users-me-channels-existing_pm .endpoint}

Retrieve a Private Message channel for a set of users, if one exists.

##### Query String Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-string-parameters) {#query-string-parameters}

Name|Description
-|-
`ids`|Comma-separated list of User IDs or @-usernames. The authenticated user can be included or excluded.


##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels/existing_pm?ids=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a channel.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "10",
    "type": "io.pnut.core.pm",
    "owner": {
      "id": "1",
      "username": "33MHz",
      "type": "human",
      "created_at": "2016-09-09T17:16:39Z",
      "timezone": "America/Chicago",
      "guid": "113BA773-F1F2-42CF-99F8-02EC778942C9",
      "locale": "en_US",
      "content": {
        "text": "This thing I do. /@pnut #tag here",
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">This thing I do. /<span data-mention-id=\"6\" data-mention-name=\"pnut\" itemprop=\"mention\">@pnut</span> <span data-tag-name=\"tag\" itemprop=\"tag\">#tag</span> here</span>",
        "entities": {
          "links": [],
          "mentions": [
            {
              "id": "6",
              "len": 6,
              "pos": 17,
              "text": "pnut",
              "is_copy": true
            }
          ],
          "tags": [
            {
              "len": 4,
              "pos": 24,
              "text": "tag"
            }
          ]
        },
        "avatar_image": {
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/4hxiGBxrSHhBzcABGX45sJxcFsHEJ_1Kq2o04iZ2-siG--l1CONPCNRvzhwW1HWXQ3DqNxyvzj4LlY1x9EJ_Or1xGGqM9iAQxFnV1lIOx6hVnq6Tm6oX714IGgovER3dYC98oLsoj7ND",
          "height": 1200,
          "width": 1200,
          "is_default": false
        },
        "cover_image": {
          "link": "https://d26y28lt6cxszo.cloudfront.net/cover/2f8b4364838cc35ea5461332cca072be1126ccbf47106353908ffbe6a994922c8086f31fff1d619d334db30240e7be474cde33e8598c172ec3d8826baf325c70d3fe897feb33",
          "height": 400,
          "width": 1024,
          "is_default": false
        }
      },
      "counts": {
        "bookmarks": 5,
        "clients": 4,
        "followers": 68,
        "following": 66,
        "posts": 937,
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
    "recent_message_id": "10",
    "acl": {
      "full": {
        "immutable": true,
        "user_ids": [],
        "you": true
      },
      "write": {
        "any_user": false,
        "immutable": true,
        "user_ids": [
          "2"
        ],
        "you": true
      },
      "read": {
        "any_user": false,
        "immutable": true,
        "public": false,
        "user_ids": [],
        "you": true
      }
    },
    "counts": {
      "messages": 1,
      "subscribers": 2
    },
    "you_subscribed": true,
    "you_muted": false,
    "has_unread": false
  }
}
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-get">GET</span> /users/me/channels/num_unread/pm [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-me-channels-num_unread-pm) {#get-users-me-channels-num_unread-pm .endpoint}

Retrieve the number of unread private messages for the authenticated user.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels/num_unread/pm" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns the number of unread channels

```json
{
  "meta": {
    "code": 200
  },
  "data": 3
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-delete">DELETE</span> /users/me/channels/num_unread/pm [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-users-me-channels-num_unread-pm) {#delete-users-me-channels-num_unread-pm .endpoint}

Mark all unread private messages as read for the authenticated user.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/channels/num_unread/pm" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE
```

Returns the number of unread channels (`0`)

```json
{
  "meta": {
    "code": 200
  },
  "data": 0
}
```