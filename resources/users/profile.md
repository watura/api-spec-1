# User Profile

Endpoints:

* [Completely update a user](#put-users-me)
* [Partially update a user](#patch-users-me)
* [Get user avatar](#get-users-id-avatar)
* [Update user avatar](#post-users-me-avatar)
* [Get user cover](#get-users-id-cover)
* [Update user cover](#post-users-me-cover)


## <span class="method method-put">PUT</span> /users/me {#put-users-me .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">update_profile</span>

Replaces the authenticated user's profile. Anything not included is removed.

Requires a user object with `application/json` Content-Type. `timezone` and `locale` are required. Not including `name` or `text` will remove them from the profile.

`text` must be a child key of `content`.

##### Example {.example-code}

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
    }" \
    -H "X-Pretty-Json: 1"
```

Returns the updated user object

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "...User Object..."
    }
}
```


## <span class="method method-patch">PATCH</span> /users/me {#patch-users-me .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">update_profile</span>

Updates only specified parts of the authenticated user's profile.

Requires a user object with `application/json` content type. `name`, `text`, `timezone`, and `locale` are current options.

`text` must be a child key of `content`.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me" \
    -X PATCH \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
        \"timezone\": \"Europe/Paris\",
        \"name\": \"Eric\"
    }" \
    -H "X-Pretty-Json: 1"
```

Returns the updated user object

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "....User Object..."
    }
}
```


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/avatar {#get-users-id-avatar .endpoint}

Scope: <span class="endpoint-meta">none</span>

This endpoint will return an HTTP 302 redirect to the user’s current avatar image. It will include any query string parameters you pass to the endpoint.

### URL Parameters

Name|Description
-|-
`user_id`|ID of the user whose avatar to retrieve

### Query String Parameters

Name|Description
-|-
`h`|Optional. The requested height to scale the image down to. Will only scale down from the `height` of the original avatar. If `w` is also set, `h` will be ignored
`w`|Optional. The requested width to scale the image down to. Will only scale down from the `width` of the original avatar..

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/@doctorlinguist/avatar" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -L
```

Returns a 302 redirect

```json

```


## <span class="method method-post">POST</span> /users/me/avatar {#post-users-me-avatar .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">update_profile</span>

Uploads a new avatar image for the authenticated user.

The uploaded image will be cropped to square and must be smaller than 2MiB.

Can specify `Content-Type` of `application/json` with the key <span class="call-param">{from_url}</span>, or a `Content-Type` of `multipart/form-data`, with the file as key `avatar`. `Content-Length` header must also be set.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/avatar" \
    -X POST \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -F "avatar=@image.png" \
    -H "X-Pretty-Json: 1"
```

Returns the updated user

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "...User Object.."
    }
}
```


## <span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/cover {#get-users-id-cover .endpoint}

Scope: <span class="endpoint-meta">none</span>

This endpoint will return an HTTP 302 redirect to the user’s current cover image. It will include any query string parameters you pass to the endpoint.

### URL Parameters

Name|Description
-|-
`user_id`|ID of the user whose cover image to retrieve

### Query String Parameters

Name|Description
-|-
`h`|Optional. The requested height to scale the image down to. Will only scale down from the `height` of the original avatar. If `w` is also set, `h` will be ignored
`w`|Optional. The requested width to scale the image down to. Will only scale down from the `width` of the original avatar.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/12/cover" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -L
```

Returns a 302 redirect

```json
--
```



## <span class="method method-post">POST</span> /users/me/cover {#post-users-me-cover .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">update_profile</span>

Uploads a new cover image for the authenticated user.

The uploaded image must be smaller than 4MiB, with a width of at least 960px and height of at least 223px.

If the width / height ratio is less than 2 to 1, the height will be cropped to height / 4.3. A 10000x10000px image would be cropped to 10000x2326px.

Can specify `Content-Type` of `application/json` with the key <span class="call-param">{from_url}</span>, or a `Content-Type` of `multipart/form-data`, with the file as key `cover`. `Content-Length` header must also be set.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/cover" \
    -X POST \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -F "cover=@image.jpg" \
    -H "X-Pretty-Json: 1"
```

Returns the updated user

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "...User Object...."
    }
}
```