# How To: User Streams

User streams are long-lasting websocket connections between the API and user-facing clients, for near-realtime interaction. They are similar to [App Streams](../resources/app-streams) but for individual users. 


## Create a Connection

To create a stream, the client must start a new websocket on the endpoint `wss://stream.pnut.io/v0/user`. The first message across this connection will be JSON like this:

```json
{
  "meta": {
    "stream": {
      "endpoint": "wss://stream.pnut.io/v0/user"
    },
    "connection_id": "5AjC6sMJrR2VueG3lHmiDTTECjzMr68i"
  }
}
```

Store the `meta.connection_id` for creating subscriptions next.


## Create Subscriptions

Now the client needs to subscribe to each endpoint you want to receive websocket responses for. Do this by calling each endpoint the same as you would if polling, once, with your `connection_id` from above included as a query parameter on the call.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/posts?connection_id=5AjC6sMJrR2VueG3lHmiDTTECjzMr68i" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X GET \
    -H "X-Pretty-Json: 1"
```

Returns the normal response from the endpoint, with `meta.subscription_id`.

```json
{
  "meta": {
    "more": true,
    "max_id": "2814",
    "min_id": "2795",
    "subscription_id": "So2e3-W76iI8nuX1UWDer_RpzVYPhxDS",
    "code": 200
  },
  "data": "..."
}
```

Currently, streams auto-delete themselves on disconnect. If you lose connection, you will have to rebuild it with subscriptions again.

A connection may have up to 16 subscriptions. A connection may subscribe to an endpoint more than once (with or without different parameters), so be sure to prevent that if it isn't helpful to you.


## Miscellaney

#### Subscribable Endpoints

* /users/me/posts
* /users/me/mentions
* /posts/:post_id/thread
* /posts/streams/me
* /posts/streams/unified
* /users/me/following
* /users/me/followers
* /channels/:channel_id/messages
* /channels *(includes new messages for channels you're subscribed to)*
* /channels/:channel_id/subscribers
* /token *(includes updates for both the token and the user objects of the current user)*
* /users/me/files

#### Connection Query Parameters

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

#### Subscription Query Parameters

* include_incomplete *(files)*
* include_private *(files)*
* channel_types
* file_types
* include_read
* include_muted
* include_deleted
* include_directed_posts


## Example Objects

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
    "subscription_ids": [
      "gJ1EUufwPXrK9N34ulTRcx5NHco6D7FE"
    ]
  },
  "data": [
    "...post object..."
  ]
}
```


### follow

Sent when any user follows or unfollows another user. Currently only a "stub", notifying you that someone followed or unfollowed, but nothing else.

```json
{
  "meta": {
    "timestamp": 1534017586,
    "subscription_ids": [
      "JUnEC5cmqiJY7Wu5uKNAmNH-AXVP6GAo"
    ]
  }
}
```


### message

Sent when a message is created or deleted from a channel.

```json
{
  "meta": {
    "timestamp": 1534019721,
    "channel_type": "io.pnut.core.pm",
    "id": "71",
    "subscription_ids": [
      "LklDY7v5zAhPYNEUZlzb01oZA_3BnYvH",
      "u7F6LFhFfTrVMBDQRkIXYPGca_I-__EW"
    ]
  },
  "data": [
    "...message object..."
  ]
}
```


### channel subscription

Sent when a user subscribes to or unsubscribes from a channel. Currently only includes the channel object, not the user whose subscription changed.

```json
{
  "meta": {
    "timestamp": 1534020228,
    "id": "22",
    "subscription_ids": [
      "_CGQ8XARMPMNqqQUaLl7GI3Utr4Bmkec"
    ]
  },
  "data": "...channel object..."
}
```


### token

Sent when you authorize a new token, or update your user object. Currently only a "stub", indicating the profile was updated, but not its details.

```json
{
  "meta": {
    "timestamp": 1534020401,
    "id": "1",
    "subscription_ids": [
      "d2Zn0uypyWVf0WCIHyLIXW0YDTtKuNOV"
    ]
  }
}
```


### file

Sent when a user uploads a file, updates file details, uploads a file, or deletes a file. Currently only a "stub", indicating that the file was uploaded, but not its details.

```json
{
  "meta": {
    "timestamp": 1534020233,
    "id": "349",
    "subscription_ids": [
      "rqDNgxAQASRCIBqHZ5Dek71SBar-wPjX"
    ]
  }
}
```