### Stream Marker

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
    
    
#### <span class="endpoint-meta"><i class="fas fa-lock"></i> any</span><span class="method method-post">POST</span> /markers [<i class="fas fa-paragraph"></i>](#post-markers) {#post-markers .endpoint}

Post a list of marker objects. You may update up to 10 at once. `id` and `name` are required. You may include `percentage` for more accuracy.
    
`id` indicates the current position of the marker. `last_read_id` indicates the *last* item in the stream that has ever been consumed by the marker. To move that in reverse, you must include the query parameter `reset_read_id=1`.
    
For a channel to be marked "read", the marker `id` must be at or greater than the current most-recent message in it.
    
##### Example Call {.example-code}
        
```bash
curl "https://api.pnut.io/v0/markers" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1" \
    -H "Content-Type: application/json" \
    -d "[
  {
    \"name\": \"channel:12\",
    \"id\": \"2593\"
  }
]"
    -X POST`
```
    
Returns a list of the updated markers
        
```json
"call for example 1"
```