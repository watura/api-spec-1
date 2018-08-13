# Text Processor

Use this endpoint to test rendering of post content. Particularly useful for debugging, or if you want to show a user exactly how the API will process their post.


## <span class="endpoint-meta"><i class="fas fa-lock"></i> any</span><span class="method method-post">POST</span> /text/process [&para;](#post-text-process) {#post-text-process .endpoint}

Submit a Content-Type of `application/json` body similar to creating a post. Returns an object containing the parsed text with entities.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/text/process" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{\"text\":\"This is a test mentioning @thrrgilag.\"}" \
    -X POST \
    -H "X-Pretty-Json: 1"
```

Returns the parsed text as it would be presented in a post

```json
"call for example 1"
```