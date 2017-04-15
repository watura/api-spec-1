### How To: Private Message

Private messages are special channels with the restricted `io.pnut.core.pm` channel type. They cannot be directly created or deactivated, and they're completely immutable. This makes the "owner" of the channel irrelevant.


#### Creation

Channel creation is handled by pnut.io.


#### Sending a Message

To send a message to other users, you need to know all of the users you will be sending the message to, or the ID of an already-created channel. If you know the channel, you may create a message in it just like you would any other channel. If you do not, or it has not been created yet, you can create an `application/json`-encoded message with the `channel_id` of "pm", and a special list in the JSON of `destinations`, listing all users by "@username" or their user ID.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/pm/messages" \
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

    
    
In every other way, they can be treated like any other channels and messages. Note that the "owner's" ID will not be in the write-access ACL, but they will not function any differently from anyone else.  

#### ACL
    
##### Example ACL {.example-code}

```json
"acl":{
  "full":{
    "immutable":true,
    "you":true,
    "user_ids":[]
  },
  "write":{
    "any_user":false,
    "immutable":true,
    "you":true,
    "user_ids":[1,5,20]
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