# How To Use App Streams

* [Create a Connection](#create-connection)
* [Subscribers, Mentions, and Notifications](#subscribers-mentions-notifications)
* [Miscellany](#miscellany)
* [Example Objects](#example-objects)


App streams are live streams of data ("firehoses") sent directly from pnut to developers' servers, to be parsed and used for end-users. Currently, the only connection option is through secure websocket.

This is the process of setting up an app stream:

1. [Create an app stream](../resources/app-streams#post-streams)
2. Set up a websocket server to listen with
3. Create a connection and start parsing the firehose

## Create a Connection {#create-connection}

To connect to a websocket, you must put a valid app access token in the query string or the Authorization header, and app stream key in the query string.

```markdown
wss://stream.pnut.io/v1/app
  ?access_token=[App Access Token]
  &key=[App Stream Key]
```

On successful connection, the API will send a message with a connection ID and the object types the stream is listening for.

```json
{
  "meta": {
    "stream": {
      "key": "butterball",
      "endpoint": "wss://stream.pnut.io/v1/app",
      "object_types": [
        "block",
        "bookmark",
        "follow",
        "message",
        "post"
      ]
    },
    "connection_id": "84Epcmo0sQzEbWEVs5_NVH1povQZUTx4"
  }
}
```

The app stream will expect to receive a message back from your server on the websocket every 60 seconds or less, to keep the connection open. If it disconnects, you will simply have to reconnect and either track your position before a disconnect and backfill with regular API calls, or skip what was missed in between.

Streams "fire and forget"; they do not guarantee you will receive every message, or receive them in chronological order.

The stream objects attempt to return objects matching what would be returned when polling, with some differences for context.

If an object is being deleted, `meta.is_deleted` is included and set `true`.

Current limitations:

* No filters; you can request a series of object types to receive, and will then receive *all* of those objects that the app is authorized to see.
* You may only have two app streams in use at a time, per client.
* Updating an app stream will not update any live websocket connections; you will have to disconnect and reconnect them.


## Subscribers, Mentions, and Notifications {#subscribers-mentions-notifications}

Messages include `meta.subscribed_user_ids`, which lists the users subscribed to that channel.

You may use the `meta.suppress_notifications` key included on posts and messages to be sure not to notify users of muted or blocked users.

Polls also include these fields when a poll is deleted or closes.


## Miscellany {#miscellany}

### Connection Query Parameters

* include_raw
* include_post_raw
* include_user_raw
* include_file_raw
* include_channel_raw
* include_message_raw
* include_bookmarked_by
* include_reposted_by
* include_marker
* include_recent_message
* include_html

### Subscription Query Parameters

* include_incomplete *(files)*
* include_private *(files)*
* channel_types
* file_types
* include_read
* include_muted
* include_deleted
* include_directed_posts


## Example Objects {#example-objects}

### post

Sent when any post is created, reposted, revised, or deleted.

Reposts will send the newly created or deleted repost and include `repost_of` in the post object.

Newly revised posts will include `meta.revision`.

Newly deleted posts will include `meta.is_deleted`.

```json
{
  "meta": {
    "timestamp": 1534019640,
    "id": "2834",
    "is_deleted": true,
    "type": "post",
    "suppress_notifications": [
      
    ]
  },
  "data": [
    "...post object..."
  ]
}
```

### bookmark

Sent when any bookmark is created or deleted.

```json
{
  "meta": {
    "timestamp": 1534016710,
    "type": "bookmark",
    "id": "2836"
  },
  "data": {
    "user": "...user who bookmarked post...",
    "post": "...post object..."
  }
}
```

### follow

Sent when any user follows or unfollows another user.

```json
{
  "meta": {
    "timestamp": 1534017586,
    "type": "follow",
    "id": "6"
  },
  "data": {
    "user": "...user doing the following...",
    "followed_user": "...user being followed..."
  }
}
```

### mute

Sent when a person who has authorized your app mutes or unmutes another user.

```json
{
  "meta": {
    "timestamp": 1534017698,
    "type": "mute",
    "id": "6"
  },
  "data": {
    "user": "...user doing the muting...",
    "muted_user": "...muted user..."
  }
}
```

### block

Sent when a person who has authorized your app blocks or unblocks another user.

```json
{
  "meta": {
    "timestamp": 1534017755,
    "type": "block",
    "id": "6"
  },
  "data": {
    "user": "...user blocking another user...",
    "blocked_user": "...blocked user..."
  }
}
```

### message

Sent when any message is created or deleted from a channel that any user is subscribed to and authorized your app access to.

`channel_type` is included in the meta.

`channel_name` is included if the channel is a chat room (of type `io.pnut.core.chat`).

`subscribed_user_ids` is included on creation, but not deletion.

```json
{
  "meta": {
    "timestamp": 1534019721,
    "channel_type": "io.pnut.core.pm",
    "id": "71",
    "type": "message",
    "subscribed_user_ids": [
      "1",
      "2"
    ],
    "suppress_notifications": [
      
    ]
  },
  "data": [
    "...message object..."
  ]
}
```

### channel

Sent when any channel is created or updated that any user is subscribed to and authorized your app access to.

```json
{
  "meta": {
    "timestamp": 1534019819,
    "id": "22",
    "type": "channel"
  },
  "data": "...channel object..."
}
```

### channel_subscription

Sent when any user who has authorized your app subscribes to or unsubscribes from a channel that they authorized your app access to.

```json
{
  "meta": {
    "timestamp": 1534020228,
    "id": "22",
    "type": "channel_subscription"
  },
  "data": {
    "user": "...user subscribing to channel...",
    "channel": "...channel object..."
  }
}
```

### poll

Sent when any poll is created, deleted, initially responded to, or closed by any user that authorized your app access to it.

Polls also include `meta.subscribed_user_ids` and `meta.suppress_notifications` for app stream notifications when a poll is deleted or closes, and `is_closed` when it is closing.

```json
{
  "meta": {
    "id": "450",
    "is_closed": true,
    "subscribed_user_ids": [
      "2",
      "6"
    ],
    "suppress_notifications": [
      
    ],
    "timestamp": 1534019819,
    "type": "poll"
  },
  "data": {
    "poll": "...poll object...",
    "user": "...user object..."
  }
}
```

### token

Sent when a user grants or revokes access to your app.

```json
{
  "meta": {
    "timestamp": 1534020401,
    "id": "1",
    "type": "token"
  },
  "data": "...token object..."
}
```

### user

Sent when a user who authorized your app updates their profile.

```json
{
  "meta": {
    "timestamp": 1534020365,
    "id": "1",
    "type": "user"
  },
  "data": "...user object..."
}
```

### file

Sent when a user authorizes uploading a file, updates file details, uploads a file, or deletes a file.

```json
{
  "meta": {
    "timestamp": 1534020233,
    "id": "349",
    "type": "file"
  },
  "data": "...file object..."
}
```
