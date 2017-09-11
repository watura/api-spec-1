### Post Threads


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /posts/<span class="call-param">{post_id}</span>/thread [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts-id-thread) {#get-posts-id-thread .endpoint}

Retrieve posts within a thread. Threads are separated by what root post all posts below it have replied to.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`post_id`|ID of the post to retrieve the thread for

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/18/thread" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts from the thread.

```json
{
  "meta": {
    "more": false,
    "max_id": "29910",
    "min_id": "18",
    "code": 200
  },
  "data": [
    {
      "created_at": "2017-03-14T18:11:25Z",
      "id": "29910",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "https:\/\/broadsword.io",
        "name": "Broadsword"
      },
      "user": {...},
      "reply_to": "29835",
      "thread_id": "18",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 0,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https:\/\/pnut.io\/schemas\/Post\"><span data-mention-id=\"321\" data-mention-name=\"sham\" itemprop=\"mention\">@sham<\/span> *waves*<br><\/span>",
        "text": "@sham *waves*\n",
        "entities": {
          "links": [
            
          ],
          "mentions": [
            {
              "id": "321",
              "len": 5,
              "pos": 0,
              "text": "sham",
              "is_leading": true
            }
          ],
          "tags": [
            
          ]
        }
      },
      "pagination_id": "29910"
    },
    {
      "created_at": "2017-03-14T17:55:00Z",
      "id": "29835",
      "source": {
        "id": "XO3CTVQl0rRMMEyo7V9JhJdUFzFDqm8o",
        "link": "https:\/\/itunes.apple.com\/us\/app\/chimpnut\/id1198300163?ls=1&mt=8",
        "name": "ChimPnut"
      },
      "user": {...},
      "reply_to": "18",
      "thread_id": "18",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 1,
        "threads": 0
      },
      "content": {
        "html": "<span itemscope=\"https:\/\/pnut.io\/schemas\/Post\"><span data-mention-id=\"12\" data-mention-name=\"po\" itemprop=\"mention\">@po<\/span> hey fancy meeting you here.<\/span>",
        "text": "@po hey fancy meeting you here.",
        "entities": {
          "links": [
            
          ],
          "mentions": [
            {
              "id": "12",
              "len": 3,
              "pos": 0,
              "text": "po",
              "is_leading": true
            }
          ],
          "tags": [
            
          ]
        }
      },
      "pagination_id": "29835"
    },
    {
      "created_at": "2016-09-11T05:17:42Z",
      "id": "18",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "https:\/\/broadsword.io",
        "name": "Broadsword"
      },
      "user": {...},
      "thread_id": "18",
      "counts": {
        "bookmarks": 0,
        "reposts": 0,
        "replies": 1,
        "threads": 1
      },
      "content": {
        "text": "A\/S\/L?\n",
        "html": "<span itemscope=\"https:\/\/pnut.io\/schemas\/Post\">A\/S\/L?\n<\/span>",
        "entities": {
          "links": [
            
          ],
          "mentions": [
            
          ],
          "tags": [
            
          ]
        }
      },
      "pagination_id": "18"
    }
  ]
}
```