# How To: ACL

Channels have three groups that determine who can read, write, and manage the channel. Users can only be within one of the three groups, and the higher-access groups inherit the lower functionality as well. Someone who can manage a channel can write and read, and someone who can write, can read. The user who creates the channel automatically and irrevocably has `full` access, but is as the `owner`, not in the ACL proper.


```json
"acl":{
  "full":{
    "immutable":false,
    "you":true,
    "user_ids":[]
  },
  "write":{
    "any_user":true,
    "immutable":false,
    "you":true,
    "user_ids":[]
  },
  "read":{
    "any_user":true,
    "immutable":false,
    "public":false,
    "you":true,
    "user_ids":[]
  }
}
```

## Permissions

### owner

* Deactivate the channel.
* Edit `full` access group.


### full

* Edit the channel and the `read` and `write` ACLs
* Delete any messages from the channel.


### write

* Write messages to the channel.


### read

* Read and subscribe to the channel and messages in it.


## Immutability

By default, all ACLs are "mutable". They can change. Once set "*im*mutable", they can no longer be changed. The exception to this is `any_user` on `read`. If `any_user` on `write` changes from false to true, `read`'s `any_user` will still inherit it.

Be sure when you create a channel not to make an ACL immutable if you think you will want to change it later.