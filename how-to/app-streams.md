### How To: App Stream

App streams are live streams of data ("firehoses") sent directly from pnut to developers' servers, to be parsed and used for end-users. Currently, the only connection option is through secure websocket.

This is the process of setting up an app stream:

* [Create an app stream](../resources/app-streams#post-streams)
* Set up a websocket server to listen with
* Point your websocket server at pnut, and start parsing the firehose

To connect to a websocket, you must put a valid app access token in the query string or the Authorization header, and app stream key in the query string.

```
wss://stream.pnut.io/v0/apps
  ?access_token=[App Access Token]
  &key=[App Stream Key]
```

On successful connection, the API will send a message with a connection ID and the object types the stream is listening for.

The app stream will expect to receive a message sent from your server every 50 seconds or less, to keep the connection open. If it disconnects, you will simply have to reconnect and either track your position before a disconnect and backfill with regular API calls, or skip what was missed in between.

Streams "fire and forget"; they do not guarantee you will receive every message, or receive them in chronological order.

The stream objects attempt to return matching objects as they would be called normally, as JSON.

If an object is being deleted, `is_deleted:true` is included in the `meta` field.

Current limitations:

* Objects do not include `raw` data
* No filters; you can request a series of object types to receive, and will then receive *all* of those object types that the app is authorized to see
* You may only have two (2) app streams in use at a time, per client
* When you update an app stream, it will not update any live websocket connections until you disconnect and reconnect them
* If you are sending notifications, you will have to track who is blocking or muting whom, currently; the API does not include who not to send a notification to. The `/apps/me/users/ids` endpoint may be helpful.


#### Example Objects

##### post

Sent when any post is created, reposted, revised, or deleted.

```json

```

##### bookmark

Sent when any bookmark is created or deleted.

```json

```

##### follow

Sent when any user follows or unfollows another user.

```json

```

##### mute

Sent when a person who has authorized your app mutes or unmutes another user.

```json

```

##### block

Sent when a person who has authorized your app blocks or unblocks another user.

```json

```

##### message

Sent when any message is created or deleted from a channel that any user is subscribed to and authorized your app access to.

`channel_type` is included in the `meta`. `subscribed_user_ids` is included on creation, but not deletion.

```json

```

##### channel

Sent when any channel is created or updated that any user is subscribed to and authorized your app access to.

```json

```

##### channel_subscription

Sent when any user who has authorized your app subscribes to or unsubscribes from a channel that they authorized your app access to.

```json

```

##### token

Sent when a user grants or revokes access to your app.

```json

```

##### user

Sent when a user who authorized your app updates their profile.

```json

```

##### file

Sent when a user authorizes uploading a file, updates file details, uploads a file, or deletes a file.

```json

```