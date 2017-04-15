### User Profile


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> update_profile</span><span class="method method-put">PUT</span> /users/me [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-users-me) {#put-users-me .endpoint}

Replaces the authenticated user's profile. Anything not included is removed.

Requires a user object with `application/json` Content-Type. `timezone` and `locale` are required. Not including `name` or `text` will remove them from the profile.

`text` must be a child key of `content`.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me" \
    -X PUT \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
        \"name\": \"Buddy\",
        \"content\": {
            \"text\": \"Good times and great oldies!\"
        },
        \"timezone\": \"America/Chicago\",
        \"locale\": \"en_US\"
    }"
```

Returns the updated user object

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "1",
    "created_at": "2016-09-09T17:16:39Z",
    "guid": "113BA773-F1F2-42CF-99F8-02EC778942C9",
    "locale": "en_US",
    "timezone": "America/Chicago",
    "type": "human",
    "username": "33MHz",
    "name": "Buddy",
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Good times and great oldies!</span>",
      "text": "Good times and great oldies!",
      "entities": {
        "links": [],
        "mentions": [],
        "tags": []
      },
      "avatar_image": {
        "height": 1200,
        "width": 1200,
        "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/4hxiGBxrSHhBzcABGX45sJxcFsHEJ_1Kq2o04iZ2-siG--l1CONPCNRvzhwW1HWXQ3DqNxyvzj4LlY1x9EJ_Or1xGGqM9iAQxFnV1lIOx6hVnq6Tm6oX714IGgovER3dYC98oLsoj7ND",
        "is_default": false
      },
      "cover_image": {
        "height": 400,
        "width": 1024,
        "link": "https://d26y28lt6cxszo.cloudfront.net/cover/2f8b4364838cc35ea5461332cca072be1126ccbf47106353908ffbe6a994922c8086f31fff1d619d334db30240e7be474cde33e8598c172ec3d8826baf325c70d3fe897feb33",
        "is_default": false
      }
    },
    "counts": {
      "bookmarks": 4,
      "clients": 4,
      "followers": 68,
      "following": 64,
      "posts": 907,
      "users": 70
    },
    "verified": {
      "domain": "codespelunkers.com",
      "link": "http://codespelunkers.com"
    },
    "follows_you": true,
    "you_blocked": false,
    "you_follow": true,
    "you_muted": false,
    "you_can_follow": false
  }
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> update_profile</span><span class="method method-patch">PATCH</span> /users/me [<i class="fa fa-paragraph" aria-hidden="true"></i>](#patch-users-me) {#patch-users-me .endpoint}

Updates only specified parts of the authenticated user's profile.

Requires a user object with `application/json` content type. `name`, `text`, `timezone`, and `locale` are current options.

`text` must be a child key of `content`.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me" \
    -X PATCH \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
        \"timezone\": \"Europe/Paris\",
        \"name\": \"Robert\"
    }"
```

Returns the updated user object

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "1",
    "created_at": "2016-09-09T17:16:39Z",
    "guid": "113BA773-F1F2-42CF-99F8-02EC778942C9",
    "locale": "en_US",
    "timezone": "Europe/Paris",
    "type": "human",
    "username": "33MHz",
    "name": "Robert",
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Good times and great oldies!</span>",
      "text": "Good times and great oldies!",
      "entities": {
        "links": [],
        "mentions": [],
        "tags": []
      },
      "avatar_image": {
        "height": 1200,
        "width": 1200,
        "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/4hxiGBxrSHhBzcABGX45sJxcFsHEJ_1Kq2o04iZ2-siG--l1CONPCNRvzhwW1HWXQ3DqNxyvzj4LlY1x9EJ_Or1xGGqM9iAQxFnV1lIOx6hVnq6Tm6oX714IGgovER3dYC98oLsoj7ND",
        "is_default": false
      },
      "cover_image": {
        "height": 400,
        "width": 1024,
        "link": "https://d26y28lt6cxszo.cloudfront.net/cover/2f8b4364838cc35ea5461332cca072be1126ccbf47106353908ffbe6a994922c8086f31fff1d619d334db30240e7be474cde33e8598c172ec3d8826baf325c70d3fe897feb33",
        "is_default": false
      }
    },
    "counts": {
      "bookmarks": 4,
      "clients": 4,
      "followers": 68,
      "following": 64,
      "posts": 907,
      "users": 70
    },
    "verified": {
      "domain": "codespelunkers.com",
      "link": "http://codespelunkers.com"
    },
    "follows_you": true,
    "you_blocked": false,
    "you_follow": true,
    "you_muted": false,
    "you_can_follow": false
  }
}
```


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/avatar [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-id-avatar) {#get-users-id-avatar .endpoint}

This endpoint will return an HTTP 302 redirect to the user’s current avatar image. It will include any query string parameters you pass to the endpoint.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`user_id`|ID of the user whose avatar to retrieve

##### Query String Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-string-parameters-1) {#query-string-parameters-1}

Name|Description
-|-
`h`|Optional. The requested height to scale the image down to. Will only scale down from the `height` of the original avatar.
`w`|Optional. The requested width to scale the image down to. Will only scale down from the `width` of the original avatar. If `h` is also set, `w` will be ignored.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/@doctorlinguist/avatar" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -L
```

Returns a 302 redirect

```json
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> update_profile</span><span class="method method-post">POST</span> /users/me/avatar [<i class="fa fa-paragraph" aria-hidden="true"></i>](#post-users-me-avatar) {#post-users-me-avatar .endpoint}

Uploads a new avatar image for the authenticated user. The uploaded image will be cropped to square and must be smaller than 2MB.

Can specify `Content-Type` of `application/json` with the key <span class="call-param">{from_url}</span>, or a `Content-Type` of `multipart/form-data`, with the file as key `avatar`. `Content-Length` header must also be set.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/avatar" \
    -X POST \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -F "avatar=@image.png"
```

Returns the updated user

```json
```


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/cover [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-id-cover) {#get-users-id-cover .endpoint}

This endpoint will return an HTTP 302 redirect to the user’s current cover image. It will include any query string parameters you pass to the endpoint.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`user_id`|ID of the user whose cover image to retrieve

##### Query String Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-string-parameters-2) {#query-string-parameters-2}

Name|Description
-|-
`h`|Optional. The requested height to scale the image down to. Will only scale down from the `height` of the original avatar.
`w`|Optional. The requested width to scale the image down to. Will only scale down from the `width` of the original avatar. If `h` is also set, `w` will be ignored.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/12/cover" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -L
```

Returns a 302 redirect

```json
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> update_profile</span><span class="method method-post">POST</span> /users/me/cover [<i class="fa fa-paragraph" aria-hidden="true"></i>](#post-users-me-cover) {#post-users-me-cover .endpoint}

Uploads a new cover image for the authenticated user. The uploaded image must be smaller than 4MB, with a width of at least 960px and height of at least 223px.

Can specify `Content-Type` of `application/json` with the key <span class="call-param">{from_url}</span>, or a `Content-Type` of `multipart/form-data`, with the file as key `cover`. `Content-Length` header must also be set.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/cover" \
    -X POST \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -F "cover=@image.jpg"
```

Returns the updated user

```json
```