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