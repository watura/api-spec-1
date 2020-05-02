# RSS

This subset of endpoints can be accessed via RSS. Note that filter query parameters will work.

* [Template URIs](#template-uris)

Endpoints:

* [Tagged posts](#get-feed-rss-posts-tags-tag)
* [User posts](#get-feed-rss-users-id-posts)
* [Post search](#get-feed-rss-posts-search)
* [Channel messages](#get-feed-rss-channels-id-messages)
* [Channel search](#get-feed-rss-channels-search)


## Template URIs {#template-uris}

URLs in the RSS feeds will by default link to post and message paths on https://beta.pnut.io. However, you may want to expose an RSS feed in your client that links to a different app. This is especially useful for custom channel types, which will not show up properly on the Beta web app.

To use template URIs in a feed, append `?uri_template=[YOUR URL]` to the feed URL. Available replacements:

* `{post_id}`
* `{channel_id}`
* `{message_id}`
* `{username}`
* `{user_id}`

For example, https://pnut.gallery uses a channel for every "gallery" in the app. It then links to a gallery like [https://pnut.gallery/media/{channel_id}/{message_id}](https://api.pnut.io/v0/feed/rss/channels/1552/messages?uri_template=https%3A%2F%2Fpnut.gallery%2Fmedia%2F%7Bchannel_id%7D%2F%7Bmessage_id%7D).



## <span class="method method-get">GET</span> /feed/rss/posts/tags/<span class="call-param">{tag}</span> {#get-feed-rss-posts-tags-tag .endpoint}

The API exposes [tagged posts](../posts/streams#get-posts-tag-tag) as RSS at `https://api.pnut.io/v0/feed/rss/posts/tags/{tag}`.


## <span class="method method-get">GET</span> /feed/rss/users/<span class="call-param">{user_id}</span>/posts {#get-feed-rss-users-id-posts .endpoint}

[A user's posts](../posts/streams#get-users-id-posts) are exposed as RSS at `https://api.pnut.io/v0/feed/rss/users/{user_id}/posts`.


## <span class="method method-get">GET</span> /feed/rss/posts/search {#get-feed-rss-posts-search .endpoint}

[Post search results](../posts/search#get-posts-search) are exposed as RSS at `https://api.pnut.io/v0/feed/rss/posts/search`.


## <span class="method method-get">GET</span> /feed/rss/channels/<span class="call-param">{channel_id}</span>/messages {#get-feed-rss-channels-id-messages .endpoint}

[Messages](../messages/lookup#get-channels-id-messages) are exposed as RSS at `https://api.pnut.io/v0/feed/rss/channels/{id}/messages`.

Note that `?access_token={token}` will have to be appended to non-public channels.


## <span class="method method-get">GET</span> /feed/rss/channels/search {#get-feed-rss-channels-search .endpoint}

[Channel search results](../channels/search#get-channels-search) are exposed as RSS at `https://api.pnut.io/v0/feed/rss/channels/search`.