### Post Lifecycle


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> write_post</span><span class="method method-post">POST</span> /posts [<i class="fa fa-paragraph" aria-hidden="true"></i>](#post-posts) {#post-posts .endpoint}

Create a post.

On creation, you can automatically update the "personal" [stream marker](../stream-marker#post-markers) to the post's ID by including `update_marker=1` in the query string.

Posts from the same human- or feed-type user cannot contain the same `text` within 120 seconds.

`JSON` in the body of the request is also allowed. Normal links and markdown links are parsed by the server by default.

##### POST Body Data [<i class="fa fa-paragraph" aria-hidden="true"></i>](#post-body-data-1) {#post-body-data-1}

Name|Description
-|-
`text`|256 character-limited string
`reply_to`|Optional ID of another post to reply to
`is_nsfw`|Optional boolean whether the post should be marked as "NSFW" (Not Safe For Work/mature/offensive)
`entities.parse_links`|Optional boolean whether the links should be parsed by the server. Default `true`
`entities.parse_markdown_links`|Optional boolean whether the markdown links should be parsed by the server. Default `true`

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -d "text=#system of a duck" \
    -X POST
```

Returns the created post.

```json
{
  "meta": {
    "code": 201
  },
  "data": {
    "created_at": "2016-12-22T14:49:16Z",
    "id": "2392",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
    "user": {...},
    "thread_id": "2392",
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
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> write_post</span><span class="method method-put">PUT</span> /posts/<span class="call-param">{post_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-posts-id) {#put-posts-id .endpoint}

Edit or "revise" a post.

* Can only be done within __300 seconds__ of the original post's creation
* Can only be done __once__ to a post
* Must contain the same [entities](../../implementation/entities) that were in the original post (Positions can change. Links can be formatted in any way, but the URLs have to be the same)

Once a revision has been made, the original post can still be retrieved from the [Revisions endpoint](lookup#get-posts-id-revisions).

Reposts made before the revision will continue to point at the original post.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`post_id`|ID of the post to retrieve

The POST body can be the same as when creating a post. `is_nsfw` *can* be changed from an initial post to a revision.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/2392" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -d "text=#system of a down" \
    -X PUT
```

Returns the revised post.

```json
{
  "meta": {
    "code": 201
  },
  "data": {
    "created_at": "2016-12-22T14:49:16Z",
    "id": "2392",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http:\/\/xyz.s3rv.com",
      "name": "Broadsword"
    },
    "user": {...},
    "thread_id": "2392",
    "is_revised": true,
    "counts": {
      "bookmarks": 0,
      "reposts": 0,
      "replies": 0,
      "threads": 0
    },
    "content": {
      "html": "<span itemscope=\"https:\/\/pnut.io\/schemas\/Post\"><span data-tag-name=\"system\" itemprop=\"tag\">#system<\/span> of a down<\/span>",
      "text": "#system of a down",
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
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> write_post</span><span class="method method-delete">DELETE</span> /posts/<span class="call-param">{post_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-posts-id) {#delete-posts-id .endpoint}

Delete a post.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`post_id`|ID of the post to delete

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/2392" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE
```

Returns the deleted post.

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "created_at": "2016-12-22T14:49:16Z",
    "id": "2392",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
    "user": {...},
    "thread_id": "2392",
    "is_revised": true,
    "counts": {
      "bookmarks": 0,
      "reposts": 0,
      "replies": 0,
      "threads": 0
    },
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-tag-name=\"system\" itemprop=\"tag\">#system</span> of a down</span>",
      "text": "#system of a down",
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
    "you_reposted": false,
    "is_deleted": true
  }
}
```