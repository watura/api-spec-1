# How To Create a Chat Room

Chat rooms are a special core Pnut channel type, `io.pnut.core.chat`. They can be searched by category in addition to the ways other channels can be searched, and also have first-party E-mail notification support.

* [Channel type](https://github.com/pnut-api/object-metadata/blob/master/channel-types/io.pnut.core.chat.md)

The channel will have to be created with the `io.pnut.core.chat-settings` raw item.

* [Chat Settings type](https://github.com/pnut-api/object-metadata/blob/master/raw/io.pnut.core.chat-settings.md)

### JSON Example Channel with Raw Item

```json
{
  "type": "io.pnut.core.chat",
  "acl": {
    "write": {
      "any_user": true
    }
  },
  "raw": {
    "io.pnut.core.chat-settings": [
      {
        "name": "Frederick's Music Lounge",
        "description": {
          "text": "A musical interlude for music-lovers"
        },
        "categories": ["community"]
      }
    ]
  }
}
```

Returns a channel object with 

```json
{
  "type": "io.pnut.core.chat",
  ...
  "raw": {
    "io.pnut.core.chat-settings": [
      {
        "name": "Frederick's Music Lounge",
        "description": {
          "entities": {
            "links": [],
            "mentions": [],
            "tags": []
          },
          "html": "<span itemscope itemtype=\"https://pnut.io/schemas/Post\">A musical interlude for music-lovers</span>",
          "text": "A musical interlude for music-lovers"
        },
        "categories": ["community"]
      }
    ]
  }
}
```


More options for the raw item are found in the community git repository linked above.

Creating a chat room is executed like any other channel, with [POST /channels](../resources/channels/lifecycle#post-channels).

### Optional Improvements to Rooms

#### Image for the Room

Images representing the room may be added with the [avatar image](https://github.com/pnut-api/object-metadata/blob/master/raw/io.pnut.core.channel.avatar.md) and [cover image](https://github.com/pnut-api/object-metadata/blob/master/raw/io.pnut.core.channel.cover.md).

#### Broadcast to Global

Clients often allow users to "broadcast" a message from a public channel to the Global post stream.

To do that, create a post with a [channel invite](https://github.com/pnut-api/object-metadata/blob/master/raw/io.pnut.core.channel.invite.md) attached, referencing the channel ID.

Then create an identical message in the channel, with a [broadcast notice](https://github.com/pnut-api/object-metadata/blob/master/raw/net.patter-app.broadcast.md) on it referencing the ID of the post that was just created.

#### 