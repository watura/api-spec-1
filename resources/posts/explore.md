### Explore Streams

Explore streams are basically pre-built searches with some simple criteria.


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /posts/streams/explore [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts-streams-explore) {#get-posts-streams-explore .endpoint}

Retrieve a list of explore streams.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/streams/explore" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of explore streams.

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {
      "description": "New conversations just starting on pnut.io",
      "link": "https://api.pnut.io/v0/posts/streams/explore/conversations",
      "slug": "conversations",
      "title": "Conversations"
    },
    {
      "description": "Random posts that never became conversations on pnut.io",
      "link": "https://api.pnut.io/v0/posts/streams/explore/missed_conversations",
      "slug": "missed_conversations",
      "title": "Missed Conversations"
    },
    {
      "description": "Posts with photos on pnut.io",
      "link": "https://api.pnut.io/v0/posts/streams/explore/photos",
      "slug": "photos",
      "title": "Photos"
    },
    {
      "description": "Posts trending on pnut.io",
      "link": "https://api.pnut.io/v0/posts/streams/explore/trending",
      "slug": "trending",
      "title": "Trending"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /posts/streams/explore/<span class="call-param">{slug}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts-streams-explore-slug) {#get-posts-streams-explore-slug .endpoint}

Retrieve a list of posts in an explore stream.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`slug`|Slug of the stream to retrieve posts from. Retrieve slugs to use from the previous call.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/streams/explore/conversations?count=1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts.

```json
{
  "meta": {
    "more": false,
    "max_id": "2445",
    "min_id": "2445",
    "code": 200
  },
  "data": [
    {
      "created_at": "2017-02-04T20:08:02Z",
      "guid": "3D6A320C-AE69-4AC7-8E54-614D3ACB4859",
      "id": "2445",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "thread_id": "2445",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 4,
        "threads": 0
      },
      "content": {
        "text": "Let\'s all go to sleep.",
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Let\'s all go to sleep.</span>",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        }
      },
      "you_bookmarked": false,
      "you_reposted": false,
      "pagination_id": "2445"
    }
  ]
}
```