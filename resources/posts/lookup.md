### Post Lookup


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts-id) {#get-posts-id .endpoint}

Retrieve a post object.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`post_id`|Post to retrieve

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/20" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a post

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "created_at": "2016-09-11T05:22:08Z",
    "id": "20",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
    "user": {...},
    "reply_to": "19",
    "thread_id": "19",
    "counts": {
      "bookmarks": 0,
      "reposts": 0,
      "replies": 0,
      "threads": 0
    },
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"12\" data-mention-name=\"po\" itemprop=\"mention\">@po</span> greetings from northern california</span>",
      "text": "@po greetings from northern california",
      "entities": {
        "links": [],
        "mentions": [
          {
            "id": "12",
            "len": 3,
            "pos": 0,
            "text": "po",
            "is_leading": true
          }
        ],
        "tags": []
      }
    },
    "you_bookmarked": false,
    "you_reposted": false
  }
}
```


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /posts [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts) {#get-posts .endpoint}

Retrieve a list of specified post objects. Only retrieves the first 200 found.

##### Query String Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-string-parameters) {#query-string-parameters}

Name|Description
-|-
`ids`|Comma-separated list of post IDs.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts?ids=20,21,4" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {
      "created_at": "2016-09-11T05:22:08Z",
      "id": "20",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "reply_to": "19",
      "thread_id": "19",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"12\" data-mention-name=\"po\" itemprop=\"mention\">@po</span> greetings from northern california</span>",
        "text": "@po greetings from northern california",
        "entities": {
          "links": [],
          "mentions": [
            {
              "id": "12",
              "len": 3,
              "pos": 0,
              "text": "po",
              "is_leading": true
            }
          ],
          "tags": []
        }
      },
      "you_bookmarked": false,
      "you_reposted": false
    },
    {
      "created_at": "2016-09-11T05:22:33Z",
      "id": "21",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "reply_to": "20",
      "thread_id": "19",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"9\" data-mention-name=\"thrrgilag\" itemprop=\"mention\">@thrrgilag</span> Hi :)\n</span>",
        "text": "@thrrgilag Hi :)\n",
        "entities": {
          "links": [],
          "mentions": [
            {
              "id": "9",
              "len": 10,
              "pos": 0,
              "text": "thrrgilag",
              "is_leading": true
            }
          ],
          "tags": []
        }
      },
      "you_bookmarked": false,
      "you_reposted": false
    },
    {
      "created_at": "2016-09-11T00:45:48Z",
      "id": "4",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "thread_id": "4",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">I received an invite to <a href=\"http://pnut.io\">pnut.io</a> today, and had boiled peanuts. Coincidence? 😋</span>",
        "text": "I received an invite to pnut.io today, and had boiled peanuts. Coincidence? 😋",
        "entities": {
          "links": [
            {
              "len": 7,
              "link": "http://pnut.io",
              "pos": 24,
              "text": "pnut.io",
              "description": "A humble short messaging service",
              "title": "pnut"
            }
          ],
          "mentions": [],
          "tags": []
        }
      },
      "you_bookmarked": false,
      "you_reposted": false
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span>/revisions [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts-id-revisions) {#get-posts-id-revisions .endpoint}

Retrieve a list of [previous versions](lifecycle#put-posts-id) of a post, not including the most recent. Currently a post can only have one previous version.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`post_id`|Post ID to retrieve any revisions of

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/2392/revisions" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {
      "id": 2392,
      "created_at": "2016-12-22 11:53:57-06",
      "thread_id": 2392,
      "user": {...},
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-tag-name=\"system\" itemprop=\"tag\">#system</span> of a duck</span>",
        "text": "#system of a duck",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": [
            {
              "len": 7,
              "pos": 0,
              "text": "system"
            }
          ]
        }
      },
      "you_bookmarked": false,
      "you_reposted": false
    }
  ]
}
```