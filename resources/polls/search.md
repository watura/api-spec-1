# Poll Search

Endpoints:

* [Search polls](#get-polls-search)


## <span class="method method-get">GET</span> /polls/search {#get-polls-search .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of polls filtered by the given criteria.

### Query Parameters [&para;](#query-parameters-1) {#query-parameters-1}

Name|Description
-|-
`order`|One of id or created_at. Default is by ID
`is_public`|If true, only include public polls
`is_anonymous`|Only include anonymous polls
`you_responded`|If true, only include polls you have responded to
`is_closed`|Only include closed polls
`poll_types`|Comma-separated list of poll types to include
`exclude_poll_types`|Comma-separated list of poll types to exclude
`raw_types`|Comma-separated list of attached raw types. Any matches returned
`user_id`|Only include polls created by this user ID

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/polls/search?is_public=1&you_responded=0&is_closed=0" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of polls

```json
"call for example 1"
```