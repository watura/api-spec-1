# Stream Marker

Endpoints:

* [Set a list of stream markers](#post-markers)

Stream markers provide a way to save a user's spot in a stream of posts or messages; a lightweight way to sync between clients, or pick up where you left off without otherwise saving it.

These are special pagination values for `since_id` and `before_id` that you must use on markable streams to actually read from its marker:

* `last_read`: the current `last_read_id` of the stream's marker
* `last_read_inclusive`
* `marker`: the current `id` of the stream's marker
* `marker_inclusive`

Current markable streams/names:

* [global](posts/streams#get-posts-streams-global): "global"
* [unified](posts/streams#get-posts-streams-unified) and [me](posts/streams#get-posts-streams-me): "personal"
* [mentions](posts/streams#get-users-id-mentions): "mentions"
* [channels](channels/lookup#get-channels-id): "channel:{id}"

On creation of posts and messages, you can automatically update the "personal" and "channel" markers to the created ID by including `update_marker=1` in the query string.


## <span class="method method-post">POST</span> /markers {#post-markers .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Post a list of marker objects. You may update up to 10 at once.

For a channel to be marked "read", the marker `id` must be at or greater than the current most-recent message in it.

### URL Parameters

Name|Description
-|-
`reset_read_id`|`id` indicates the current position of the marker. `last_read_id` indicates the *last* item in the stream that has ever been consumed by the marker. To move that in reverse, this must be set True

### POST Body Data

Name|Description
-|-
`id`|__Required__ The ID of the object in the stream you want to mark as having read most recently
`name`|__Required__ What marker to update for a user. E.g., the global stream is `global`, or a channel would be `channel:{id}`
`percentage`|Can specify 1-100 percent of the current `id` has been read or positioned in a stream.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v1/markers" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1" \
    -H "Content-Type: application/json" \
    -d "[
  {
    \"name\": \"channel:12\",
    \"id\": \"2593\"
  }
]"
    -X POST
```

Returns a list of the updated markers

```json
{
    "meta": {
        "code": 200
    },
    "data": [
        {
            "id": "0",
            "last_read_id": "0",
            "percentage": 0,
            "updated_at": "ISO-8601",
            "version": "String",
            "name": "String"
        }
    ]
}
```
