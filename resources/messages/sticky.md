### Sticky Messages

"Sticky" messages are like bookmarks for a channel, but they are per-channel, not per-user. They will have `is_sticky: true`.

Users with `full` access to a channel are able to sticky and un-sticky messages in the channel.



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-get">GET</span> /channels/<span class="call-param">{channel_id}</span>/sticky_messages [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-channels-id-sticky_messages) {#get-channels-id-sticky_messages .endpoint}

Retrieve sticky messsages in a channel. The requesting user must have access to the channel.

Note that the `pagination_id` and `min_id` and `max_id` will change as users sticky and un-sticky messages.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the channel to retrieve messages from


##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/sticky_messages" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of messages.

```json
{
  "meta": {
    "more": false,
    "max_id": "2",
    "min_id": "1",
    "code": 200
  },
  "data": [
    {
      "id": "15",
      "channel_id": "5",
      "created_at": "2016-12-28T21:16:02Z",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "is_sticky": true,
      "thread_id": "15",
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
      "pagination_id": "2"
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
      "pagination_id": "1"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-put">PUT</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span>/sticky [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-channels-id-messages-id-sticky) {#put-channels-id-messages-id-sticky .endpoint}

Sticky a message.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`channel_id`|ID of the channel the message is in
`message_id`|Message to sticky


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/messages/13/sticky" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT
```

Returns the bookmarked post.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "13",
    "channel_id": "5",
    "created_at": "2016-12-28T21:06:13Z",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
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
    "is_sticky": true
  }
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> messages</span><span class="method method-delete">DELETE</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span>/sticky [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-channels-id-messages-id-sticky) {#delete-channels-id-messages-id-sticky .endpoint}

Un-sticky a message.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`channel_id`|ID of the channel the message is in
`message_id`|Message to un-sticky

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/5/messages/13/sticky" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE
```

Returns the message.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "13",
    "channel_id": "5",
    "created_at": "2016-12-28T21:06:13Z",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
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
    }
  }
}
```