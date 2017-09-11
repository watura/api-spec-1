### Reposts

Reposting is a special action. Reposts act as complete posts in themselves, with the "original" post embedded as an additional object. Unlike normal posts, actions (reply, repost, bookmark) cannot be executed against a repost.

#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> write_post</span><span class="method method-put">PUT</span> /posts/<span class="call-param">{post_id}</span>/repost [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-posts-id-repost) {#put-posts-id-repost .endpoint}

Repost another post. The repost will show up in followers' streams if they have not seen another repost of the same within the last week, and if the reposted post is not in their recent stream. It is created in its own thread, not the thread of the original post. This increments a user's post count.
    
##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`post_id`|ID of the post to repost
    
##### Example Call {.example-code}
        
```bash
curl "https://api.pnut.io/v0/posts/2370/repost" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT
```
    
Returns the reposted post.
        
```json
{
  "meta": {
    "code": 201
  },
  "data": {
    "created_at": "2016-11-23T15:54:51Z",
    "id": "2370",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
    "user": {...},
    "reply_to": "2368",
    "thread_id": "2367",
    "counts": {
      "bookmarks": 0,
      "reposts": 1,
      "replies": 1,
      "threads": 0
    },
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"1\" data-mention-name=\"33MHz\" itemprop=\"mention\">@33MHz</span> Can&#039;t wait. You got big plans?</span>",
      "text": "@33MHz Can\'t wait. You got big plans?",
      "entities": {
        "links": [],
        "mentions": [
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
    "you_bookmarked": false,
    "you_reposted": true
  }
}
```    
    
    
#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> write_post</span><span class="method method-delete">DELETE</span> /posts/<span class="call-param">{post_id}</span>/repost [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-posts-id-repost) {#delete-posts-id-repost .endpoint}

Delete a repost. The actual repost is completely deleted; it does not leave behind a thread or deleted post to look up.
    
Users can also delete their own reposts even if they no longer have access to the original post (e.g., they were blocked). In that case, the returned post in the `data` field is simply `{"id":POST_ID,"you_reposted":false}`.
    
##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`post_id`|ID of the post to delete a repost for
    
##### Example Call {.example-code}
        
```bash
curl "https://api.pnut.io/v0/posts/2370/repost" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE
```
        
Returns the previously reposted post.
        
```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "created_at": "2016-11-23T15:54:51Z",
    "id": "2370",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
    "user": {...},
    "reply_to": "2368",
    "thread_id": "2367",
    "counts": {
      "bookmarks": 0,
      "reposts": 0,
      "replies": 1,
      "threads": 0
    },
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"1\" data-mention-name=\"33MHz\" itemprop=\"mention\">@33MHz</span> Can&#039;t wait. You got big plans?</span>",
      "text": "@33MHz Can\'t wait. You got big plans?",
      "entities": {
        "links": [],
        "mentions": [
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
    "you_bookmarked": false,
    "you_reposted": false
  }
}
```