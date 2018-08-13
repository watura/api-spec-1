# Poll Lifecycle

For an explanation of how to attach polls to other objects, read [How To File](../../how-to/file). Functionally they are almost identical: Create a poll and use the `+io.pnut.core.poll` replacement raw value on a `io.pnut.core.poll-notice` raw item.

You may also look at the [GitHub object-metadata](https://github.com/pnut-api/object-metadata/blob/master/raw-replacement-values/%2Bio.pnut.core.poll.md).



## <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> polls,write_post</span><span class="method method-post">POST</span> /polls [&para;](#post-polls) {#post-polls .endpoint}

Create a poll placeholder or a complete poll. `type`, `prompt`, `options`, and `duration` or `closed_at` are necessary. By default, the poll will be private and anonymous.

Content-Type of `application/json`.

### POST Body Data [&para;](#post-body-data-1) {#post-body-data-1}

Name|Description
-|-
`prompt`|__Required__ 256-character explanation or question for the `options` (to be displayed and attached to the object)
`type`|__Required__ Reverse domain name-style identifier of the poll type. E.g., `com.example.site`
`options`|__Required__ List of 2 to 10 options must be specified, each with `text` and optional `position` (if you want to specify their order)
`closed_at`|__Required__ (if `duration` not set) ISO 8601 timestamp at least 1 minute and no more than 2 weeks in the future, after which no one can respond to it
`duration`|__Required__ (if `closed_at` not set) number of minutes the poll should be open, minimum of 1 and maximum of 20160
`is_public`|If true, poll is public
`is_anonymous`|If false, user IDs will be identified in the final poll


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/polls" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
  \"type\":\"com.example.site\",
  \"prompt\":\"Do you like Pnut?\",
  \"options\":[
    {
      \"text\":\"Yes\"
    },
    {
      \"text\":\"Of course\"
    }
  ],
  \"duration\":\"60\",
  \"is_anonymous\":\"false\"
}" \
    -X POST \
    -H "X-Pretty-Json: 1"
```

Returns the created poll

```json
"call for example 1"
```



## <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> polls,write_post</span><span class="method method-put">PUT</span> /polls/<span class="call-param">{poll_id}</span>/response/<span class="call-param">{position} [&para;](#put-polls-id-response-position) {#put-polls-id-response-position .endpoint}

Respond to a poll.

Only human-type accounts may respond to polls.

### URL Parameters [&para;](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`poll_id`|ID of the poll to respond to
`position`|Position of the position to respond with

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/polls/1/response/2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns poll on success

```json

```




## <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> polls</span><span class="method method-delete">DELETE</span> /polls/<span class="call-param">{poll_id}</span> [&para;](#delete-polls-id) {#delete-polls-id .endpoint}

Delete a poll. This will not disassociate a poll with any other objects (posts, messages...).

### URL Parameters [&para;](#url-parameters-3) {#url-parameters-3}

Name|Description
-|-
`poll_id`|ID of the poll to delete

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/polls/72" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the deleted poll

```json
"call for example 3"
```
