### Messages Lookup



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-channels-id-messages-id) {#get-channels-id-messages-id .endpoint}

Retrieve a message from a channel. The requesting user must have access to the channel or have created the message.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the channel to retrieve a message from.
`message_id`|ID of the message to retrieve.


##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/messages/11" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns the requested message.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "11",
    "channel_id": "5",
    "created_at": "2016-12-17T16:51:14Z",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
    "thread_id": "11",
    "user": {...},
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\">test</span>",
      "text": "test",
      "entities": {
        "mentions": [],
        "links": [],
        "tags": []
      }
    },
    "counts": {
      "replies": 0
    }
  }
}
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span>/thread [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-channels-id-messages-id-thread) {#get-channels-id-messages-id-thread .endpoint}

Retrieve messages in the same thread of a channel. All messages will have the same `thread_id` (they are all replies to the same post, or is not a reply to any post). The requesting user must have access to the channel.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the channel to retrieve messages from.
`message_id`|ID of the message whose thread to retrieve.


##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/messages/13/thread" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of messages.

```json
{
  "meta": {
    "more": false,
    "max_id": "16",
    "min_id": "13",
    "code": 200
  },
  "data": [
    {
      "id": "16",
      "channel_id": "5",
      "created_at": "2017-01-04T01:51:40Z",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "reply_to": "13",
      "thread_id": "13",
      "user": {...},
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">test 2</span>",
        "text": "test 2",
        "entities": {
          "mentions": [],
          "links": [],
          "tags": []
        }
      },
      "counts": {
        "replies": 0
      },
      "pagination_id": "16"
    },
    {
      "id": "13",
      "channel_id": "5",
      "created_at": "2016-12-28T21:06:13Z",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "is_sticky": true,
      "thread_id": "13",
      "user": {...},
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">another post here</span>",
        "text": "another post here",
        "entities": {
          "mentions": [],
          "links": [],
          "tags": []
        }
      },
      "counts": {
        "replies": 0
      },
      "pagination_id": "13"
    }
  ]
}
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-get">GET</span> /channels/messages [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-messages) {#get-messages .endpoint}

Retrieve a list of specified messages. Will only return the first 200 found.

##### Query String Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-string-parameters) {#query-string-parameters}

Name|Description
-|-
`ids`|Comma-separated list of message IDs.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/messages?ids=4,11,12" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of the messages found.

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {
      "id": "4",
      "channel_id": "2",
      "created_at": "2016-11-25T02:29:29Z",
      "source": {
        "id": "UU6mkUMMHq1JNHfiReoUNkeaZjKDp2LQ",
        "link": "http://test.s3rv.com",
        "name": "PHP"
      },
      "thread_id": "4",
      "user": {...},
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"2\" data-mention-name=\"wife\" itemprop=\"mention\">@wife</span> how&#039;s this again?</span>",
        "text": "@wife how\'s this again?",
        "entities": {
          "mentions": [
            {
              "len": 5,
              "pos": 0,
              "text": "wife",
              "id": "2",
              "is_leading": true,
              "is_copy": true
            }
          ],
          "links": [],
          "tags": []
        }
      },
      "counts": {
        "replies": 0
      }
    },
    {
      "id": "11",
      "channel_id": "5",
      "created_at": "2016-12-17T16:51:14Z",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "thread_id": "11",
      "user": {...},
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">test</span>",
        "text": "test",
        "entities": {
          "mentions": [],
          "links": [],
          "tags": []
        }
      },
      "counts": {
        "replies": 0
      }
    },
    {
      "id": "12",
      "channel_id": "5",
      "created_at": "2016-12-17T17:13:51Z",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "is_deleted": true,
      "thread_id": "12",
      "user": {...},
      "counts": {
        "replies": 0
      }
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/messages [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-channels-id-messages) {#get-channels-id-messages .endpoint}

Retrieve paginated messages from a channel.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`channel_id`|ID of the channel to retrieve messages from

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/2/messages" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of messages from the channel.

```json
{
  "meta": {
    "more": false,
    "max_id": "12",
    "min_id": "11",
    "code": 200
  },
  "data": [
    {
      "id": "12",
      "channel_id": "5",
      "created_at": "2016-12-17T17:13:51Z",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "is_deleted": true,
      "thread_id": "12",
      "user": {...},
      "counts": {
        "replies": 0
      },
      "pagination_id": "12"
    },
    {
      "id": "11",
      "channel_id": "5",
      "created_at": "2016-12-17T16:51:14Z",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "thread_id": "11",
      "user": {...},
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">test</span>",
        "text": "test",
        "entities": {
          "mentions": [],
          "links": [],
          "tags": []
        }
      },
      "counts": {
        "replies": 0
      },
      "pagination_id": "11"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-get">GET</span> /users/me/messages [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-me-messages) {#get-users-me-messages .endpoint}

Retrieve a paginated list of messages created by the authenticated user.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/messages" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of messages.

```json
{
  "meta": {
    "more": false,
    "max_id": "12",
    "min_id": "6",
    "code": 200
  },
  "data": [
    {
      "id": "12",
      "channel_id": "5",
      "created_at": "2016-12-17T17:13:51Z",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "is_deleted": true,
      "thread_id": "12",
      "user": {...},
      "counts": {
        "replies": 0
      },
      "pagination_id": "12"
    },
    {
      "id": "11",
      "channel_id": "5",
      "created_at": "2016-12-17T16:51:14Z",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "thread_id": "11",
      "user": {...},
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">test</span>",
        "text": "test",
        "entities": {
          "mentions": [],
          "links": [],
          "tags": []
        }
      },
      "counts": {
        "replies": 0
      },
      "pagination_id": "11"
    },
    {
      "id": "7",
      "channel_id": "6",
      "created_at": "2016-11-25T18:05:30Z",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "thread_id": "7",
      "user": {...},
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">testing!</span>",
        "text": "testing!",
        "entities": {
          "mentions": [],
          "links": [],
          "tags": []
        }
      },
      "counts": {
        "replies": 0
      },
      "pagination_id": "7"
    },
    {
      "id": "6",
      "channel_id": "2",
      "created_at": "2016-11-25T02:29:50Z",
      "source": {
        "id": "UU6mkUMMHq1JNHfiReoUNkeaZjKDp2LQ",
        "link": "http://test.s3rv.com",
        "name": "PHP"
      },
      "thread_id": "6",
      "user": {...},
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"2\" data-mention-name=\"wife\" itemprop=\"mention\">@wife</span> how&#039;s this again?</span>",
        "text": "@wife how\'s this again?",
        "entities": {
          "mentions": [
            {
              "len": 5,
              "pos": 0,
              "text": "wife",
              "id": "2",
              "is_leading": true,
              "is_copy": true
            }
          ],
          "links": [],
          "tags": []
        }
      },
      "counts": {
        "replies": 0
      },
      "pagination_id": "6"
    }
  ]
}
```