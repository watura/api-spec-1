### Post Streams



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> stream</span><span class="method method-get">GET</span> /posts/streams/me [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts-streams-me) {#get-posts-streams-me .endpoint}

The authenticated user's stream of posts from their followers and themself.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/streams/me?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts.

```json
{
  "meta": {
    "more": true,
    "max_id": "2384",
    "min_id": "2383",
    "code": 200
  },
  "data": [
    {
      "created_at": "2016-12-11T18:14:12Z",
      "guid": "E0C85794-D8E8-44CA-90F2-E34D8CA1A96D",
      "id": "2384",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "thread_id": "2384",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">this is a test</span>",
        "text": "this is a test",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        }
      },
      "you_bookmarked": false,
      "you_reposted": false,
      "pagination_id": "2384"
    },
    {
      "created_at": "2016-11-25T22:42:26Z",
      "guid": "51C581B0-C03A-41FE-8641-8A5EED549E4F",
      "id": "2383",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "thread_id": "2383",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">test with <a href=\"https://pnut.io/updates#2016-11-24.a\">link</a> [pnut.io] </span>",
        "text": "test with link [pnut.io] ",
        "links_not_parsed": true,
        "entities": {
          "links": [
            {
              "amended_len": 14,
              "len": 4,
              "link": "https://pnut.io/updates#2016-11-24.a",
              "pos": 10,
              "text": "link"
            }
          ],
          "mentions": [],
          "tags": []
        }
      },
      "you_bookmarked": false,
      "you_reposted": false,
      "pagination_id": "2383"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> stream</span><span class="method method-get">GET</span> /posts/streams/unified [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts-streams-unified) {#get-posts-streams-unified .endpoint}

A combined Personal Stream including the authenticated user's mentions.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/streams/unified" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts.

```json
{
  "meta": {
    "more": true,
    "max_id": "2384",
    "min_id": "2383",
    "code": 200
  },
  "data": [
    {
      "created_at": "2016-12-11T18:14:12Z",
      "guid": "E0C85794-D8E8-44CA-90F2-E34D8CA1A96D",
      "id": "2384",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "thread_id": "2384",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">this is a test</span>",
        "text": "this is a test",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        }
      },
      "you_bookmarked": false,
      "you_reposted": false,
      "pagination_id": "2384"
    },
    {
      "created_at": "2016-11-25T22:42:26Z",
      "guid": "51C581B0-C03A-41FE-8641-8A5EED549E4F",
      "id": "2383",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "thread_id": "2383",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">test with <a href=\"https://pnut.io/updates#2016-11-24.a\">link</a> [pnut.io] </span>",
        "text": "test with link [pnut.io] ",
        "links_not_parsed": true,
        "entities": {
          "links": [
            {
              "amended_len": 14,
              "len": 4,
              "link": "https://pnut.io/updates#2016-11-24.a",
              "pos": 10,
              "text": "link"
            }
          ],
          "mentions": [],
          "tags": []
        }
      },
      "you_bookmarked": false,
      "you_reposted": false,
      "pagination_id": "2383"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/mentions [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-id-mentions) {#get-users-id-mentions .endpoint}

Posts mentioning the specified user.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`user_id`|Posts mention this user

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/9/mentions?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts.

```json
{
  "meta": {
    "more": true,
    "max_id": "2357",
    "min_id": "2346",
    "code": 200
  },
  "data": [
    {
      "created_at": "2016-11-22T16:24:17Z",
      "guid": "B2478FF7-2FEC-41E8-B715-050A8967F6D2",
      "id": "2357",
      "source": {
        "id": "_ZF0GARr13lyeXrQHZNLQBKuQ1MT-VNi",
        "link": "http://test.s3rv.com",
        "name": "Robin Alpha"
      },
      "user": {...},
      "reply_to": "2335",
      "thread_id": "2296",
      "counts": {
        "bookmarks": 1,
        "reposts": 0,
        "replies": 1,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"1\" data-mention-name=\"33MHz\" itemprop=\"mention\">@33MHz</span> <span data-mention-id=\"9\" data-mention-name=\"thrrgilag\" itemprop=\"mention\">@thrrgilag</span> If it requires some kind of install process in a specific browser it does not make a difference whether it&#039;s app or extension. But which browser is important, so same level as OS for mobile.</span>",
        "text": "@33MHz @thrrgilag If it requires some kind of install process in a specific browser it does not make a difference whether it\'s app or extension. But which browser is important, so same level as OS for mobile.",
        "entities": {
          "links": [],
          "mentions": [
            {
              "id": "9",
              "len": 10,
              "pos": 7,
              "text": "thrrgilag",
              "is_leading": true
            },
            {
              "id": "1",
              "len": 6,
              "pos": 0,
              "text": "33MHz",
              "is_leading": true
            }
          ],
          "tags": []
        }
      },
      "you_bookmarked": true,
      "you_reposted": false,
      "pagination_id": "2357"
    },
    {
      "created_at": "2016-11-22T01:48:00Z",
      "guid": "D1673EEA-EE04-4751-B0C5-D85D83D22405",
      "id": "2346",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "reply_to": "2342",
      "thread_id": "2338",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"9\" data-mention-name=\"thrrgilag\" itemprop=\"mention\">@thrrgilag</span> Hah. I could add an E-mail notification option for &quot;on edit of a post I reposted&quot;.</span>",
        "text": "@thrrgilag Hah. I could add an E-mail notification option for \"on edit of a post I reposted\".",
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
      "you_reposted": false,
      "pagination_id": "2346"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/posts [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-id-posts) {#get-users-id-posts .endpoint}

Posts created by the specified user.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`user_id`|Posts created by this user

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/9/posts?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts.

```json
{
  "meta": {
    "more": true,
    "max_id": "2373",
    "min_id": "2369",
    "code": 200
  },
  "data": [
    {
      "created_at": "2016-11-23T16:59:24Z",
      "guid": "50FC8A55-F408-427D-9640-F50A9FE4B4DC",
      "id": "2373",
      "source": {
        "id": "RG2OXsxanFOD0pPZ2oURY3OS3zUVixho",
        "link": "https://monkeystew.org",
        "name": "CMDr Monkey"
      },
      "user": {...},
      "thread_id": "2373",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Qt Creator in my eyeballs, deadmau5 in my ears, and <span data-tag-name=\"coffee\" itemprop=\"tag\">#coffee</span> in my bloodstream. I call that a good start.</span>",
        "text": "Qt Creator in my eyeballs, deadmau5 in my ears, and #coffee in my bloodstream. I call that a good start.",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": [
            {
              "len": 7,
              "pos": 52,
              "text": "coffee"
            }
          ]
        }
      },
      "you_bookmarked": false,
      "you_reposted": false,
      "pagination_id": "2373"
    },
    {
      "created_at": "2016-11-23T15:31:57Z",
      "guid": "356A9FA3-B96A-4B4B-B050-181A0AA86451",
      "id": "2369",
      "source": {
        "id": "RG2OXsxanFOD0pPZ2oURY3OS3zUVixho",
        "link": "https://monkeystew.org",
        "name": "CMDr Monkey"
      },
      "user": {...},
      "thread_id": "2369",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Good morning all. Day before a US holiday, no meetings, and everyone I work with is off today. Guess I&#039;ll have all sorts of available time.</span>",
        "text": "Good morning all. Day before a US holiday, no meetings, and everyone I work with is off today. Guess I\'ll have all sorts of available time.",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        }
      },
      "you_bookmarked": false,
      "you_reposted": false,
      "pagination_id": "2369"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /posts/streams/global [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts-streams-global) {#get-posts-streams-global .endpoint}

A stream of all users' public posts.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/streams/global?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts.

```json
{
  "meta": {
    "more": true,
    "max_id": "2384",
    "min_id": "2383",
    "code": 200
  },
  "data": [
    {
      "created_at": "2016-12-11T18:14:12Z",
      "guid": "E0C85794-D8E8-44CA-90F2-E34D8CA1A96D",
      "id": "2384",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "thread_id": "2384",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">this is a test</span>",
        "text": "this is a test",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        }
      },
      "you_bookmarked": false,
      "you_reposted": false,
      "pagination_id": "2384"
    },
    {
      "created_at": "2016-11-25T22:42:26Z",
      "guid": "51C581B0-C03A-41FE-8641-8A5EED549E4F",
      "id": "2383",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "thread_id": "2383",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">test with <a href=\"https://pnut.io/updates#2016-11-24.a\">link</a> [pnut.io] </span>",
        "text": "test with link [pnut.io] ",
        "links_not_parsed": true,
        "entities": {
          "links": [
            {
              "amended_len": 14,
              "len": 4,
              "link": "https://pnut.io/updates#2016-11-24.a",
              "pos": 10,
              "text": "link"
            }
          ],
          "mentions": [],
          "tags": []
        }
      },
      "you_bookmarked": false,
      "you_reposted": false,
      "pagination_id": "2383"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /posts/tag/<span class="call-param">{tag}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts-tag-tag) {#get-posts-tag-tag .endpoint}

A stream of all posts that include the specified `tag`.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-3) {#url-parameters-3}

Name|Description
-|-
`tag`|The string tag that all posts should include

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/tag/MondayNightDanceParty?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts.

```json
{
  "meta": {
    "more": false,
    "max_id": "2034",
    "min_id": "1220",
    "code": 200
  },
  "data": [
    {
      "created_at": "2016-11-08T03:23:02Z",
      "guid": "BDAA9DD5-1C12-48A7-9024-BDA42EE49944",
      "id": "2034",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "thread_id": "2034",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-tag-name=\"MondayNightDanceParty\" itemprop=\"tag\">#MondayNightDanceParty</span>\nRight here:\n<a href=\"http://vidcast-app.net/view.html#event=70604691\">http://vidcast-app.net/view.html#event=70604691</a>\nRight now!</span>",
        "text": "#MondayNightDanceParty\nRight here:\nhttp://vidcast-app.net/view.html#event=70604691\nRight now!",
        "entities": {
          "links": [
            {
              "len": 47,
              "link": "http://vidcast-app.net/view.html#event=70604691",
              "pos": 35,
              "text": "http://vidcast-app.net/view.html#event=70604691",
              "title": "VC powered by @chatview & App.net. Follow @vidcast for updates"
            }
          ],
          "mentions": [],
          "tags": [
            {
              "len": 22,
              "pos": 0,
              "text": "MondayNightDanceParty"
            }
          ]
        }
      },
      "you_bookmarked": false,
      "you_reposted": false,
      "pagination_id": "2034"
    },
    {
      "created_at": "2016-10-17T15:01:28Z",
      "guid": "41069845-2A2A-4DF6-9904-98EC9C55E4AA",
      "id": "1220",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "thread_id": "1220",
      "counts": {
        "bookmarks": 0,
        "reposts": 1,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-tag-name=\"MONDAYNIGHTDANCEPARTY\" itemprop=\"tag\">#MONDAYNIGHTDANCEPARTY</span></span>",
        "text": "#MONDAYNIGHTDANCEPARTY",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": [
            {
              "len": 22,
              "pos": 0,
              "text": "MONDAYNIGHTDANCEPARTY"
            }
          ]
        }
      },
      "you_bookmarked": false,
      "you_reposted": true,
      "pagination_id": "1220"
    }
  ]
}
```