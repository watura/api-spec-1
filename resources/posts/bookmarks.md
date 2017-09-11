### Post Bookmarks

Bookmarking is an action for users to keep track of posts. You can see others' bookmarks as well.

#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> any</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/bookmarks [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-id-bookmarks) {#get-users-id-bookmarks .endpoint}

Retrieve a list of bookmarks made by the specified user.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`user_id`|What user's bookmarks to look up

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/1/bookmarks" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts.

```json
{
  "meta": {
    "more": true,
    "max_id": "1845",
    "min_id": "1835",
    "code": 200
  },
  "data": [
    {
      "created_at": "2016-11-23T20:50:11Z",
      "id": "2375",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "http://xyz.s3rv.com",
        "name": "Broadsword"
      },
      "user": {...},
      "thread_id": "2375",
      "counts": {
        "bookmarks": 1,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Well on my way with Channels. A couple minor things to add, then lots of testing, figure out where I went wrong, fix that, and finish dotting a couple i&#039;s.</span>",
        "text": "Well on my way with Channels. A couple minor things to add, then lots of testing, figure out where I went wrong, fix that, and finish dotting a couple i\'s.",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        }
      },
      "you_bookmarked": true,
      "you_reposted": false,
      "pagination_id": "1845"
    },
    {
      "created_at": "2016-11-22T16:39:29Z",
      "id": "2359",
      "source": {
        "id": "fNGJi3HD3IMZQKQ3ryvmt54SsciGlEnt",
        "link": "https://monkeystew.org",
        "name": "Goober"
      },
      "user": {...},
      "thread_id": "2359",
      "counts": {
        "bookmarks": 1,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">&quot;Sometimes I use common sense, which is against government regulations.&quot; -lead inspector</span>",
        "text": "\"Sometimes I use common sense, which is against government regulations.\" -lead inspector",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        }
      },
      "you_bookmarked": true,
      "you_reposted": false,
      "pagination_id": "1835"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> write_post</span><span class="method method-put">PUT</span> /posts/<span class="call-param">{post_id}</span>/bookmark [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-posts-id-bookmark) {#put-posts-id-bookmark .endpoint}

Bookmark a post.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`post_id`|Post to bookmark

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/2375/bookmark" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT
```

Returns the bookmarked post.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "created_at": "2016-11-23T20:50:11Z",
    "id": "2375",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
    "user": {...},
    "thread_id": "2375",
    "counts": {
      "bookmarks": 2,
      "reposts": 0,
      "replies": 0,
      "threads": 0
    },
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Well on my way with Channels. A couple minor things to add, then lots of testing, figure out where I went wrong, fix that, and finish dotting a couple i&#039;s.</span>",
      "text": "Well on my way with Channels. A couple minor things to add, then lots of testing, figure out where I went wrong, fix that, and finish dotting a couple i\'s.",
      "entities": {
        "links": [],
        "mentions": [],
        "tags": []
      }
    },
    "you_bookmarked": true,
    "you_reposted": false
  }
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> write_post</span><span class="method method-delete">DELETE</span> /posts/<span class="call-param">{post_id}</span>/bookmark [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-posts-id-bookmark) {#delete-posts-id-bookmark .endpoint}

Delete a bookmark.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`post_id`|Post to delete a bookmark for

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/2375/bookmark" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE
```

Returns the post a bookmark was removed from.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "created_at": "2016-11-23T20:50:11Z",
    "id": "2375",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
    "user": {...},
    "thread_id": "2375",
    "counts": {
      "bookmarks": 1,
      "reposts": 0,
      "replies": 0,
      "threads": 0
    },
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Well on my way with Channels. A couple minor things to add, then lots of testing, figure out where I went wrong, fix that, and finish dotting a couple i&#039;s.</span>",
      "text": "Well on my way with Channels. A couple minor things to add, then lots of testing, figure out where I went wrong, fix that, and finish dotting a couple i\'s.",
      "entities": {
        "links": [],
        "mentions": [],
        "tags": []
      }
    },
    "you_bookmarked": false,
    "you_reposted": false
  }
}
```