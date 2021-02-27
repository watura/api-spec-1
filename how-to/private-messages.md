# How To Use Private Messages

Private messages are created in special channels with the restricted `io.pnut.core.pm` channel type. This is a list of ways they are different from normal channels:

* They cannot be directly created or deactivated
* They're always immutable (you cannot change who is included in the channel)
* There is no `user`/owner, only users with `write` access
* Any user can "sticky" a message


## Channel Creation

Pnut automatically creates the channel when a private message is sent. If there has already been a message between the same parties previously, Pnut reuses the existing channel.


## Sending a Message

To send a message to other users, you need to know all of the users you will be sending the message to, or the ID of an already-created channel. If you know the channel ID, you may create a message in it just like you would any other channel. If you do not, or it has not been created yet, you can create an `application/json`-encoded message with the `channel_id` of `pm`, and a special list in the JSON of `destinations`, listing all users by "@username" or their user ID.

Here, the destinations are for user IDs `1` and `5`, and username `@ericd`:

```bash
curl "https://api.pnut.io/v1/channels/pm/messages" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
  \"text\":\"We should make great things.\",
  \"destinations\":[
    1,5,\"@ericd\"
  ]
}" \
    -X POST
```

This is what the example's channel permissions would look like if User ID `2` created the message:
    
```json
"acl":{
  "full":{
    "immutable":true,
    "you":false,
    "user_ids":[]
  },
  "write":{
    "any_user":false,
    "immutable":true,
    "you":true,
    "user_ids":[1,2,5,20]
  },
  "read":{
    "any_user":false,
    "immutable":true,
    "public":false,
    "you":true,
    "user_ids":[]
  }
}
```

The creating user's ID will be in the write-access ACL, just like everyone else.

In every other way, they can be treated like other channels and messages.


## Existing PM Channels

If you want to see a PM channel between specific users without sending a message, you can use the [Existing PM endpoint](../resources/channels/lookup#get-users-me-channels-existing_pm) to find the channel ID.