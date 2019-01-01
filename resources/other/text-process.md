# Text Processor

Use this endpoint to test rendering of post content. Particularly useful for debugging, or if you want to show a user exactly how the API will process their post.

Endpoints:

* [Test text processing](#post-text-process)


## <span class="method method-post">POST</span> /text/process {#post-text-process .endpoint}

Scopes: <span class="endpoint-meta">any</span>

Submit a Content-Type of `application/json` body as if creating a post. Returns an object containing the parsed text with entities.

### Query String Parameters

Name|Description
-|-
`object_type`|`post` or `message`. By default, `text` character length is restricted to 256, like a post. You may change it to rendering like a message with up to 2048 characters by including this parameter with a value of `message`.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/text/process" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{\"text\":\"This is a test mentioning @thrrgilag.\"}" \
    -X POST \
    -H "X-Pretty-Json: 1"
```

Returns the parsed text similar to how it would be presented in a post

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "text": "...",
        "links": [],
        "tags": [],
        "mentions": [],
        "html": "<span itemscope itemtype=\"https://pnut.io/schemas/Post\">...</span>"
    }
}
```