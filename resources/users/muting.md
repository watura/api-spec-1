#### User Muting

Muting a user will prevent them from being visible to the muting user unless specifically requested.



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> any</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/muted [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-id-muted) {#get-users-id-muted .endpoint}

Retrieve a list of muted users. Users may only see their own list of muted users.
    
##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`user_id`|ID of the user whose list of muted users to retrieve
    
##### Example Call {.example-code}
    
```bash
curl "https://api.pnut.io/v0/users/me/muted" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```
            
Returns a list of users
            
```json
{
  "meta": {
    "more": false,
    "max_id": "1482443879",
    "min_id": "1482443879",
    "code": 200
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
      "you_blocked": false,
      "you_follow": false,
      "you_muted": true,
      "you_can_follow": true,
      "pagination_id": "1482443879"
    }
  ]
}
```
    

#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> follow</span><span class="method method-put">PUT</span> /users/<span class="call-param">{user_id}</span>/mute [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-users-id-mute) {#put-users-id-mute .endpoint}

Mute a user. Muted users will not appear in future requests.
    
##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`user_id`|ID of the user to mute
    
##### Example Call {.example-code}
        
```bash
curl "https://api.pnut.io/v0/users/2/mute" \
    -X PUT \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```
            
Returns the muted user
            
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
    "you_muted": true,
    "you_can_follow": true
  }
}
```
    
    
#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> follow</span><span class="method method-delete">DELETE</span> /users/<span class="call-param">{user_id}</span>/mute [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-users-id-mute) {#delete-users-id-mute .endpoint}

Unmute a user.
    
##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-3) {#url-parameters-3}

Name|Description
-|-
`user_id`|ID of the user to unmute
    
##### Example Call {.example-code}
        
```bash
curl "https://api.pnut.io/v0/users/2/mute" \
    -X DELETE \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```
            
Returns the unmuted user
            
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