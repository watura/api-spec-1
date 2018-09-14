# RSS

This subset of endpoints can be accessed via RSS. Note that filter query parameters will work.


## Tagged Posts

The API exposes [tagged posts](../posts/streams#get-posts-tag-tag) as RSS at `https://api.pnut.io/v0/feed/rss/posts/tags/{tag}`.


## User Posts

[A user's posts](../posts/streams#get-users-id-posts) are exposed as RSS at `https://api.pnut.io/v0/feed/rss/users/{id}/posts`.


## Post Search

[Post search results](../posts/search#get-posts-search) are exposed as RSS at `https://api.pnut.io/v0/feed/rss/posts/search`.


## Channel Messages

[Messages](../messages/lookup#get-channels-id-messages) are exposed as RSS at `https://api.pnut.io/v0/feed/rss/channels/{id}/messages`.

Note that `?access_token={token}` will have to be appended to non-public channels.