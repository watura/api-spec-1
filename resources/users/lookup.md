#### User Lookup


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-id) {#get-users-id .endpoint}

Retrieve a user object.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`user_id`|*User ID or username with "@" symbol* of the user to retrieve

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns the user object

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "1",
    "created_at": "2016-09-09T17:16:39Z",
    "guid": "113BA773-F1F2-42CF-99F8-02EC778942C9",
    "locale": "en",
    "timezone": "America/Chicago",
    "type": "human",
    "username": "33MHz",
    "name": "Robert",
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"6\" data-mention-name=\"pnut\" itemprop=\"mention\">@pnut</span> developer. Coder by day, coder by night.</span>",
      "text": "@pnut developer. Coder by day, coder by night.",
      "entities": {
        "links": [],
        "mentions": [
          {
            "id": "6",
            "len": 5,
            "pos": 0,
            "text": "pnut",
            "is_leading": true
          }
        ],
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


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /users [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users) {#get-users .endpoint}

Retrieve a list of specified user objects. Only retrieves the first 200 found.

##### Query String Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-string-parameters) {#query-string-parameters}

Name|Description
-|-
`ids`|Comma-separated list of user IDs. IDs are required; no other identifiers are allowed.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users?ids=4,12,1000" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of users

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {
      "id": "4",
      "created_at": "2016-09-10T18:01:21Z",
      "guid": "8F530358-2B30-48E6-8F1F-756EAAA0B05A",
      "locale": "en_CA",
      "timezone": "Europe/Berlin",
      "type": "human",
      "username": "shawn",
      "name": "Shawn Throop",
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">A Canadian, a dancer with Staatstheater N&uuml;rnberg, and a wannabe iOS developer when I get the time.</span>",
        "text": "A Canadian, a dancer with Staatstheater Nürnberg, and a wannabe iOS developer when I get the time.",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        },
        "avatar_image": {
          "height": 640,
          "width": 640,
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/XGm9r9JA6NYRAtuwEyjQT7PuwXe00uSIi6hQVqIbW1JxHA2wVzV1YitMrXEvJK1YXfmcfNchBytu2u8_mFbjUhXE0_s6sEYxKfYFOzg8oQZHqVtiWA4gH66jFwOSbXGVYIYKefOBjTZT",
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
        "bookmarks": 2,
        "clients": 1,
        "followers": 10,
        "following": 3,
        "posts": 21,
        "users": 0
      },
      "verified": {
        "domain": "shawnthroop.com",
        "link": "http://shawnthroop.com"
      },
      "follows_you": true,
      "you_blocked": false,
      "you_follow": true,
      "you_muted": false,
      "you_can_follow": true
    },
    {
      "id": "12",
      "created_at": "2016-09-11T00:11:51Z",
      "guid": "5487A956-D731-4783-821D-AD8AF4A66F01",
      "locale": "en_US",
      "timezone": "America/Chicago",
      "type": "human",
      "username": "po",
      "content": {
        "avatar_image": {
          "height": 200,
          "width": 200,
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/n79OLeONW-Pjwlr7pfWF-00UafyiEFc94cHbL7GG6XzmGSHOFYIQi7-CrShtoZeiHoJAfyfZ_-aBs7m6A6Bap07McRpmzBOYBt34N-s6ZKlxpwFPsZ-y1YcidJDD94ud74kg0NM1GEyS",
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
        "following": 4,
        "posts": 17,
        "users": 0
      },
      "follows_you": true,
      "you_blocked": false,
      "you_follow": true,
      "you_muted": false,
      "you_can_follow": true
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> app</span><span class="method method-get">GET</span> /apps/me/users/ids [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-apps-me-users-ids) {#get-apps-me-users-ids .endpoint}

Retrieve a list of all user IDs that authorize the requesting app. It is not paginated.

Requires an app token.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/apps/me/users/ids" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of user IDs

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    "2","5","18"
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> app</span><span class="method method-get">GET</span> /apps/me/users/tokens [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-apps-me-users-tokens) {#get-apps-me-users-tokens .endpoint}

Retrieve a list of all user token objects that authorize the requesting app. Not currently paginated.

Requires an app token.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/apps/me/users/tokens" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of user tokens

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {
      "app": {
        "id": "_ZF0GARfe2tyy43hfgds3g43g1MT-VNi",
        "link": "https://broadsword.io",
        "name": "Broadsword"
      },
      "scopes": [
        "write_post",
        "update_profile",
        "stream",
        "follow"
      ],
      "user": {
        "id": "1",
        "username": "33MHz",
        "type": "human",
        "created_at": "2016-09-09T17:16:39Z",
        "timezone": "America/Chicago",
        "guid": "113BA773-F1F2-42CF-99F8-02EC778942C9",
        "locale": "en_US",
        "content": {
          "text": "This thing I do. /@pnut #tag here",
          "html": "<span itemscope=\"https://pnut.io/schemas/Post\">This thing I do. /<span data-mention-id=\"6\" data-mention-name=\"pnut\" itemprop=\"mention\">@pnut</span> <span data-tag-name=\"tag\" itemprop=\"tag\">#tag</span> here</span>",
          "entities": {
            "links": [],
            "mentions": [
              {
                "id": "6",
                "len": 6,
                "pos": 17,
                "text": "pnut",
                "is_copy": true
              }
            ],
            "tags": [
              {
                "len": 4,
                "pos": 24,
                "text": "tag"
              }
            ]
          },
          "avatar_image": {
            "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/4hxiGBxrSHhBzcABGX45sJxcdfsdfgweg04iZ2-siG--l1CONPCNRvzhwW1HWXQ3DqNxyvzj4LlY1x9EJ_Or1xGGqM9iAQxFnV1lIOx6hVnq6Tm6oX714IGgovER3dYC98oLsoj7ND",
            "height": 1200,
            "width": 1200,
            "is_default": false
          },
          "cover_image": {
            "link": "https://d26y28lt6cxszo.cloudfront.net/cover/2f8b4364838cc35ea5461jksalaikjkl2h3jh3jf47106353908ffbe6a994922c8086f31fff1d619d334db30240e7be474cde33e8598c172ec3d8826baf325c70d3fe897feb33",
            "height": 400,
            "width": 1024,
            "is_default": false
          }
        },
        "counts": {
          "bookmarks": 6,
          "clients": 4,
          "followers": 67,
          "following": 64,
          "posts": 1044,
          "users": 70
        },
        "verified": {
          "domain": "codespelunkers.com",
          "link": "http://codespelunkers.com"
        }
      },
      "pagination_id": 151
    }
  ]
}
```