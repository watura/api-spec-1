### Text Processor

Use this endpoint to test rendering of post content. Particularly useful for debugging, or if you want to show a user exactly how the API will process their post.


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> any</span><span class="method method-post">POST</span> /text/process [<i class="fa fa-paragraph" aria-hidden="true"></i>](#post-text-process) {#post-text-process .endpoint}

Submit a Content-Type of `application/json` body similar to creating a post. Returns an object containing the parsed text with entities.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/text/process" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{\"text\":\"This is a test mentioning @thrrgilag.\"}" \
    -X POST
```

Returns the parsed text as it would be presented in a post

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "text": "This is a test mentioning @thrrgilag.",
    "links": [],
    "tags": [],
    "mentions": [
      {
        "id": "9",
        "len": 10,
        "pos": 26,
        "text": "thrrgilag"
      }
    ],
    "html": "<span itemscope=\"https://pnut.io/schemas/Post\">This is a test mentioning <span data-mention-id=\"9\" data-mention-name=\"thrrgilag\" itemprop=\"mention\">@thrrgilag</span>.</span>"
  }
}
```