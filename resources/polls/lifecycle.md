# Poll Lifecycle

For an explanation of how to attach polls to other objects, read [How To File](../../how-to/file). Functionally they are almost identical: Create a poll and use the `+io.pnut.core.poll` replacement raw value on a `io.pnut.core.poll-notice` raw item.

You may also look at the [GitHub object-metadata](https://github.com/pnut-api/object-metadata/blob/master/raw-replacement-values/%2Bio.pnut.core.poll.md).

Endpoints:

* [Create a poll](#post-polls)
* [Respond to a poll](#put-polls-id-response-position)
* [Delete a poll](#delete-polls-id)


## <span class="method method-post">POST</span> /polls {#post-polls .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">polls,write_post</span>

Create a poll placeholder or a complete poll. `type`, `prompt`, `options`, and `duration` or `closed_at` are necessary. By default, the poll will be private and anonymous.

Content-Type of `application/json`.

### POST Body Data

Name|Description
-|-
`prompt`|__Required__ 256-character explanation or question for the `options` (to be displayed and attached to the object)
`type`|__Required__ Reverse domain name-style identifier of the poll type. E.g., `com.example.site`
`options`|__Required__ List of 2 to 10 options must be specified, each with `text` and optional `position` (if you want to specify their order)
`closed_at`|__Required__ (if `duration` not set) ISO 8601 timestamp at least 1 minute and no more than 2 weeks in the future, after which no one can respond to it
`duration`|__Required__ (if `closed_at` not set) number of minutes the poll should be open, minimum of 1 and maximum of 20160
`is_public`|If true, poll is public
`is_anonymous`|If false, user IDs will be identified in the final poll
`max_options`|Number of options a user can respond with, between 1 and one less than number of `options`


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
{
    "meta": {
        "code": 201
    },
    "data": {"...Poll Object..."}
}
```



## <span class="method method-put">PUT</span> /polls/<span class="call-param">{poll_id}</span>/response {#put-polls-id-response .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">polls,write_post</span>

Respond to a poll.

Only human-type accounts may respond to polls.

If a poll is private, you must inherently have access to the poll to respond, or include a `poll_token` in the query string. Polls attached to posts, for example, always include `poll_token` in the raw data. Since you might not know if a poll is public or private in such a case, you should always include the poll token when you have it.

Responses can be changed until the poll closes.

### URL Parameters

Name|Description
-|-
`poll_id`|ID of the poll to respond to

### Query Parameters

Name|Description
-|-
`poll_token`|Required on private polls when you don't know or aren't guaranteed access

### POST Body Data

Name|Description
-|-
`positions`|Positions of the options to respond with

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/polls/1/response" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{\"positions\": [1,3]}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns poll on success

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...Poll Object..."}
}
```



## <span class="method method-put">PUT</span> /polls/<span class="call-param">{poll_id}</span>/response/<span class="call-param">{position}</span> {#put-polls-id-response-position .endpoint}

__Deprecated__: Please use the above multiple-option response endpoint.

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">polls,write_post</span>

Respond to a poll.

Only human-type accounts may respond to polls.

If a poll is private, you must inherently have access to the poll to respond, or include a `poll_token` in the query string. Polls attached to posts, for example, always include `poll_token` in the raw data. Since you might not know if a poll is public or private in such a case, you should always include the poll token when you have it.

Responses can be changed until the poll closes.

### URL Parameters

Name|Description
-|-
`poll_id`|ID of the poll to respond to
`position`|Position of the position to respond with

### Query Parameters

Name|Description
-|-
`poll_token`|Required on private polls when you don't know or aren't guaranteed access

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/polls/1/response/2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns poll on success

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...Poll Object..."}
}
```




## <span class="method method-delete">DELETE</span> /polls/<span class="call-param">{poll_id}</span> {#delete-polls-id .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">polls</span>

Delete a poll. This will not disassociate a poll with any other objects (posts, messages...).

### URL Parameters

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
{
    "meta": {
        "code": 200
    },
    "data": {"....Poll Object..."}
}
```
