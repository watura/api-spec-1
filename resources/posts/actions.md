### Post Actions

Bookmarks, Replies, and Reposts


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span>/actions [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts-id-actions) {#get-posts-id-actions .endpoint}

Retrieve actions executed against a post.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`post_id`|ID of the post to retrieve actions for

##### Query Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-parameters-1) {#query-parameters-1}

Name|Description
-|-
`filters`|Comma-separated list of actions to filter by
`exclude`|Comma-separated list of actions to exclude. `?exclude=bookmark` will return all actions except bookmarks. If `filters` is also specified, this is ignored.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/83/actions" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of actions.

```json
{
  "meta": {
    "more": false,
    "max_id": "38",
    "min_id": "38",
    "code": 200
  },
  "data": [
    {
      "pagination_id": "38",
      "event_date": "2016-09-12T18:44:53Z",
      "action": "reply",
      "users": [
        {...}
      ]
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> any</span><span class="method method-get">GET</span> /users/me/actions [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-me-actions) {#get-users-me-actions .endpoint}

Retrieve actions executed against the authenticated user and their posts.

##### Query Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-parameters-2) {#query-parameters-2}

Name|Description
-|-
`filters`|Comma-separated list of actions to filter by. `?filters=bookmark` will only include bookmarks.
`exclude`|Comma-separated list of actions to exclude. `?exclude=bookmark` will return all actions except bookmarks. If `filters` is also specified, this is ignored.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/actions" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of actions.

```json
{
  "meta": {
    "more": false,
    "max_id": "1854",
    "min_id": "1838",
    "code": 200
  },
  "data": [
    {
      "pagination_id": "1854",
      "event_date": "2016-12-01T04:08:06Z",
      "action": "follow",
      "users": [
        {...}
      ],
      "objects": [
        {...}
      ]
    },
    {
      "pagination_id": "1845",
      "event_date": "2016-11-23T20:54:59Z",
      "action": "bookmark",
      "users": [
        {...}
      ],
      "objects": [
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
          "you_bookmarked": false,
          "you_reposted": false
        }
      ]
    },
    {
      "pagination_id": "1842",
      "event_date": "2016-11-23T15:54:51Z",
      "action": "reply",
      "users": [
        {...}
      ],
      "objects": [
        {
          "created_at": "2016-11-23T14:18:47Z",
          "id": "2368",
          "source": {
            "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
            "link": "http://xyz.s3rv.com",
            "name": "Broadsword"
          },
          "user": {...},
          "reply_to": "2367",
          "thread_id": "2367",
          "counts": {
            "bookmarks": 0,
            "reposts": 0,
            "replies": 1,
            "threads": 0
          },
          "content": {
            "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"49\" data-mention-name=\"jasonechols\" itemprop=\"mention\">@jasonechols</span> yow! Good day to you, too. Thanksgiving incoming.</span>",
            "text": "@jasonechols yow! Good day to you, too. Thanksgiving incoming.",
            "entities": {
              "links": [],
              "mentions": [
                {
                  "id": "49",
                  "len": 12,
                  "pos": 0,
                  "text": "jasonechols",
                  "is_leading": true
                }
              ],
              "tags": []
            }
          },
          "you_bookmarked": false,
          "you_reposted": false
        }
      ]
    },
    {
      "pagination_id": "1838",
      "event_date": "2016-11-22T23:48:06Z",
      "action": "reply",
      "users": [
        false
      ],
      "objects": [
        {
          "created_at": "2016-11-22T14:20:06Z",
          "id": "2356",
          "source": {
            "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
            "link": "http://xyz.s3rv.com",
            "name": "Broadsword"
          },
          "user": {...},
          "thread_id": "2356",
          "counts": {
            "bookmarks": 0,
            "reposts": 0,
            "replies": 1,
            "threads": 0
          },
          "content": {
            "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"67\" data-mention-name=\"keita\" itemprop=\"mention\">@keita</span> <a href=\"https://keita.blog\">https://keita.blog</a> works here. ;)</span>",
            "text": "@keita https://keita.blog works here. ;)",
            "entities": {
              "links": [
                {
                  "len": 18,
                  "link": "https://keita.blog",
                  "pos": 7,
                  "text": "https://keita.blog",
                  "description": "Just Another Sleepy Programmer",
                  "title": "Keita\'s Blog"
                }
              ],
              "mentions": [
                {
                  "id": "67",
                  "len": 6,
                  "pos": 0,
                  "text": "keita",
                  "is_leading": true
                }
              ],
              "tags": []
            }
          },
          "you_bookmarked": false,
          "you_reposted": false
        }
      ]
    }
  ]
}
```