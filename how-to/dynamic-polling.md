# How To: Dynamic Polling Streams

When polling a stream of posts like the global feed, or messages in a channel, there is a way to catch updates on deleted and revised posts.

When polling with `since_id` set, the `meta` object on the stream will include lists `meta.deleted_ids` and `meta.revised_ids` if a post is deleted or revised, respectively, since the ID of `since_id` was created.

For example: my client is making the request `curl "https://api.pnut.io/v0/posts/streams/global?since_id=500"`, when `500` is the latest post in the stream. Someone deletes their post `244`. The next time my client requests global with `since_id=500`, this is what I get back:

```json
{
  "meta": {
    "more": false,
    "code": 200,
    "deleted_ids": [
 	  "244"
    ]
  },
  "data": []
}
```

Knowing this, my client can determine if post `244` is being displayed, and update its view to show that the post is now deleted.

The same is true for revised posts, and deleted messages. The client knowing that a post is revised, it could automatically make a call to `GET /posts?ids=244`, for whatever posts were revised that were also being displayed.

This is most useful when a client is polling forward, though; note that the sample of deleted and revised posts is not capped going forward. If you made a call with `since_id=200` and 40 posts had been deleted since post `200` was created, you would get all of those IDs. So it is not very useful when a client is pulling up old, cached posts (a fresh request of old posts would include the deleted or revised posts' most recent state, rendering "updates" like these irrelevant).