### User Blocking

Blocking a user prevents the blocked user and the blocking user from seeing each other on the network except in a few necessary places.


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> any</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/blocked [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-id-blocked) {#get-users-id-blocked .endpoint}

Retrieve a list of blocked users. Users may only see their own list of blocked users.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`user_id`|ID of the user whose list of blocked users to retrieve

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/blocked" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of users

```json
{
  "meta": {
    "more": false,
    "max_id": "1482441540",
    "min_id": "1480009992"
  },
  "data": [
    {
      "id": "2",
      "created_at": "2016-09-10T12:41:21Z",
      "locale": "en_US",
      "timezone": "America/Chicago",
      "type": "human",
      "username": "Wife",
      "name": "Anna",
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">We\'re getting outta this madhouse</span>",
        "text": "We\'re getting outta this madhouse",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        },
        "avatar_image": {
          "height": 1456,
          "width": 1456,
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/rv0ORwZMYgadj74hz0eotcUuGZKKYy2O7CuplRFsrb3yo_T-TD1UYmo7j3brXq8K-VmRkv9pLRovHp1i25X7ZNO_Joo-ATXlcnIPmRehZLLyPC7LEuN5UGHetqV9qcYkHTcPzAVNgSIM",
          "is_default": false
        },
        "cover_image": {
          "height": 223,
          "is_default": true,
          "link": "https://d26y28lt6cxszo.cloudfront.net/cover/default_cover",
          "width": 960
        }
      },
      "counts": {
        "bookmarks": 1,
        "clients": 0,
        "followers": 9,
        "following": 18,
        "posts": 19,
        "users": 1
      },
      "follows_you": false,
      "you_blocked": true,
      "you_follow": false,
      "you_muted": false,
      "you_can_follow": false,
      "pagination_id": "1482441540"
    },
    {
      "id": "67",
      "created_at": "2016-10-26T03:38:08Z",
      "locale": "en_US",
      "timezone": "Asia/Tokyo",
      "type": "human",
      "username": "keita",
      "content": {
        "avatar_image": {
          "is_default": true,
          "height": 512,
          "width": 512,
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/CZDpIXTs9kub-4m1op3e0qmEmFL0T1zoThYFFpqDU-8eXgpnZW2eP1JCCcLhuXRkG4lk9RocnH3vTDaukEp5s3_wWDPj9Hvi2s_5pkRkm45atQxwEpnGgFhrm36xoc-nYgRtxRljsMts"
        },
        "cover_image": {
          "height": 223,
          "is_default": true,
          "link": "https://d26y28lt6cxszo.cloudfront.net/cover/default_cover",
          "width": 960
        }
      },
      "counts": {
        "bookmarks": 0,
        "clients": 0,
        "followers": 3,
        "following": 0,
        "posts": 2,
        "users": 0
      },
      "follows_you": false,
      "you_blocked": true,
      "you_follow": true,
      "you_muted": false,
      "you_can_follow": false,
      "pagination_id": "1480009992"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> follow</span><span class="method method-put">PUT</span> /users/<span class="call-param">{user_id}</span>/block [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-users-id-block) {#put-users-id-block .endpoint}

Block a user. Blocked users will not show up in future requests, the same as if they were muted. Blocked users also cannot retrieve this authorized user in their requests. Can do so even if the other user is blocking you (but will only return an ID of the blocked user).

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`user_id`|ID of the user to block

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/2/block" \
    -X PUT \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns the blocked user

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "2",
    "created_at": "2016-09-10T12:41:21Z",
    "locale": "en_US",
    "timezone": "America/Chicago",
    "type": "human",
    "username": "Wife",
    "name": "Anna",
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\">We\'re getting outta this madhouse</span>",
      "text": "We\'re getting outta this madhouse",
      "entities": {
        "links": [],
        "mentions": [],
        "tags": []
      },
      "avatar_image": {
        "height": 1456,
        "width": 1456,
        "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/rv0ORwZMYgadj74hz0eotcUuGZKKYy2O7CuplRFsrb3yo_T-TD1UYmo7j3brXq8K-VmRkv9pLRovHp1i25X7ZNO_Joo-ATXlcnIPmRehZLLyPC7LEuN5UGHetqV9qcYkHTcPzAVNgSIM",
        "is_default": false
      },
      "cover_image": {
        "height": 223,
        "is_default": true,
        "link": "https://d26y28lt6cxszo.cloudfront.net/cover/default_cover",
        "width": 960
      }
    },
    "counts": {
      "bookmarks": 1,
      "clients": 0,
      "followers": 9,
      "following": 18,
      "posts": 19,
      "users": 1
    },
    "follows_you": false,
    "you_blocked": true,
    "you_follow": false,
    "you_muted": false,
    "you_can_follow": false
  }
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> follow</span><span class="method method-delete">DELETE</span> /users/<span class="call-param">{user_id}</span>/block [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-users-id-block) {#delete-users-id-block .endpoint}

Unblock a user. Can do so even if the other user is blocking you (but will only return an ID of the blocked user).

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-3) {#url-parameters-3}

Name|Description
-|-
`user_id`|ID of the user to unblock

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/2/block" \
    -X DELETE \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns the unblocked user

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "2",
    "created_at": "2016-09-10T12:41:21Z",
    "locale": "en_US",
    "timezone": "America/Chicago",
    "type": "human",
    "username": "Wife",
    "name": "Anna",
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\">We\'re getting outta this madhouse</span>",
      "text": "We\'re getting outta this madhouse",
      "entities": {
        "links": [],
        "mentions": [],
        "tags": []
      },
      "avatar_image": {
        "height": 1456,
        "width": 1456,
        "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/rv0ORwZMYgadj74hz0eotcUuGZKKYy2O7CuplRFsrb3yo_T-TD1UYmo7j3brXq8K-VmRkv9pLRovHp1i25X7ZNO_Joo-ATXlcnIPmRehZLLyPC7LEuN5UGHetqV9qcYkHTcPzAVNgSIM",
        "is_default": false
      },
      "cover_image": {
        "height": 223,
        "is_default": true,
        "link": "https://d26y28lt6cxszo.cloudfront.net/cover/default_cover",
        "width": 960
      }
    },
    "counts": {
      "bookmarks": 1,
      "clients": 0,
      "followers": 9,
      "following": 18,
      "posts": 19,
      "users": 1
    },
    "follows_you": false,
    "you_blocked": false,
    "you_follow": false,
    "you_muted": false,
    "you_can_follow": true
  }
}
```