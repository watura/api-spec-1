# Explore Streams

Explore streams are pre-built searches with some simple criteria.

Endpoints:

* [Get a list of explore streams](#get-channels-streams-explore)
* [Get an explore stream](#get-channels-streams-explore-slug)


## <span class="method method-get">GET</span> /channels/streams/explore {#get-channels-streams-explore .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of explore streams.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/streams/explore" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of explore streams.

```json
{
    "meta": {
        "code": 200
    },
    "data": [
        {
            "description": "String",
            "slug": "String",
            "title": "String",
            "url": "https://example.com"
        }
    ]
}
```


## <span class="method method-get">GET</span> /channels/streams/explore/<span class="call-param">{slug}</span> {#get-channels-streams-explore-slug .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of channels in an explore stream.

### URL Parameters

Name|Description
-|-
`slug`|Slug of the stream to retrieve channels from. Retrieve slugs to use from the previous call.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/channels/streams/explore/conversations?count=1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of channels.

```json
{
    "meta": {
        "more": true,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...Channel Object..."}
    ]
}
```