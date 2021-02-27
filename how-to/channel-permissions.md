# How To Manage Channel Permissions

Channels have three groups that determine who can read, write, and manage the channel: `full`, `write`, `read`.

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

Users can't be in multiple groups. The higher-access groups inherit the lower functionality as well; someone who can manage a channel can write and read, and someone who can write, can read.

The user who creates the channel automatically has `full` access, but is the `user` in the channel object, not in the ACL proper. The owner can be changed later.


## Permissions

### user

* Deactivate the channel
* Edit `full` access group
* Change the owner of the channel


### full

* Edit the channel and the `read` and `write` ACLs
* Delete any messages from the channel


### write

* Write messages to the channel


### read

* Read and subscribe to the channel and messages in it


## Immutability

By default, all ACLs are "mutable". They can change. Once set "*im*mutable", they can no longer be changed.

The exception to this is `read.any_user`, which will still inherit `write.any_user` changing to `true` even if `read.immutable: true`.

When you create a channel, be sure not to make an ACL immutable if you think you will want to change it later.