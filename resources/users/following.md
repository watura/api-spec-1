#### User Following


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> any</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/following [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-id-following) {#get-users-id-following .endpoint}

Retrieve a list of user objects that the specified user is following.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`user_id`|ID of the user whose following to retrieve

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/2/following?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of users

```json
{
  "meta": {
    "more": true,
    "max_id": "1479396935",
    "min_id": "1479180531",
    "code": 200
  },
  "data": [
    {
      "id": "71",
      "created_at": "2016-11-02T16:28:37Z",
      "locale": "en_US",
      "timezone": "America/Chicago",
      "type": "human",
      "username": "pnutapi",
      "name": "pnut.io API",
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Changes involving the <a href=\"http://pnut.io\">pnut.io</a> API.\r\n\r\nRun by <span data-mention-id=\"1\" data-mention-name=\"33MHz\" itemprop=\"mention\">@33MHz</span></span>",
        "text": "Changes involving the pnut.io API.\r\n\r\nRun by @33MHz",
        "entities": {
          "links": [
            {
              "len": 7,
              "link": "http://pnut.io",
              "pos": 22,
              "text": "pnut.io"
            }
          ],
          "mentions": [
            {
              "id": "1",
              "len": 6,
              "pos": 45,
              "text": "33MHz"
            }
          ],
          "tags": []
        },
        "avatar_image": {
          "is_default": true,
          "height": 512,
          "width": 512,
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/K3LiyDFxdI6fzxmUKAc5em8jkvzBUMYTZ-fwnVl7MMvE6Sb_LMoFts7aZ4Ttr8vUeQ9kjOFCIodmYvl4v-Iv9wLsXf7vzvunbAGDt0A5SLFBQ14DoV3hOt43N1Mvzg5NFXfTa8U4viWX"
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
        "followers": 4,
        "following": 1,
        "posts": 1,
        "users": 0
      },
      "follows_you": false,
      "you_blocked": false,
      "you_follow": true,
      "you_muted": false,
      "you_can_follow": true,
      "pagination_id": "1479396935"
    },
    {
      "id": "75",
      "created_at": "2016-11-15T03:28:51Z",
      "locale": "en",
      "timezone": "America/New_York",
      "type": "human",
      "username": "charlesg",
      "name": "Charles G",
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Hello Kitty superfan. Tell my mother I&#039;m coming home: I&#039;ve been destroyed by hippie powers.</span>",
        "text": "Hello Kitty superfan. Tell my mother I\'m coming home: I\'ve been destroyed by hippie powers.",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        },
        "avatar_image": {
          "height": 1944,
          "width": 1944,
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/YcsuqTOXx5dJ4Cx9ePV6nsOyy9k6LqAMpEiVL66n6TV75Ad55Xya0qcYi5-LEO9O4jdMBCfOpLWfHbjm_LlvTxYEGxHkwck7CUfBqNDxHmBKY77HP5zJTIEjTMkxDNRdyIp6s3U3voYV",
          "is_default": false
        },
        "cover_image": {
          "height": 753,
          "width": 4320,
          "link": "https://d26y28lt6cxszo.cloudfront.net/cover/dc8aa86619c8e6ef60fd638d8f20d0aef8355046a4dc7de2e505ba91a2f4b4e558abd4cc847ed59ddd4f7b26bb2932d8394b0864b6a7870e2f5a1e50c8c5c3a1f0cc9c3e9726",
          "is_default": false
        }
      },
      "counts": {
        "bookmarks": 1,
        "clients": 0,
        "followers": 3,
        "following": 2,
        "posts": 5,
        "users": 0
      },
      "follows_you": true,
      "you_blocked": false,
      "you_follow": true,
      "you_muted": false,
      "you_can_follow": true,
      "pagination_id": "1479180531"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> any</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/followers [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-id-followers) {#get-users-id-followers .endpoint}

Retrieve a list of user objects that are following the specified user.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`user_id`|ID of the user whose followers to retrieve


##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/@shawn/followers?count=2" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of users

```json
{
  "meta": {
    "more": true,
    "max_id": "1479179225",
    "min_id": "1479039055",
    "code": 200
  },
  "data": [
    {
      "id": "58",
      "created_at": "2016-10-18T14:43:20Z",
      "locale": "en_US",
      "timezone": "America/Chicago",
      "type": "human",
      "username": "thedoctor",
      "name": "Doctor",
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Wanderer in the fourth dimension. </span>",
        "text": "Wanderer in the fourth dimension. ",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        },
        "avatar_image": {
          "height": 600,
          "width": 600,
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/yy8MeA2JLhh5DnuG_IB4qQ4QUD7dkMBBDtokFtOrP-MbNrutx9AMuWIjtlNpGfIKKwLpFPrzY-bauynSPTHnFhE5hPyBClX5UlX66AnaZMBPEGQRSOF_xLa4cx7moN-Ng4IumHJKbu84",
          "is_default": false
        },
        "cover_image": {
          "height": 127,
          "width": 976,
          "link": "https://d26y28lt6cxszo.cloudfront.net/cover/f4a8dbdd0e751350b370d5f00340eb46cab55942625b172cecfe94e14e50341e2793f0ba49b3c564caf5ad117177c1de426ac5433395c3921835002026b7a3831c2f1693fcc1",
          "is_default": false
        }
      },
      "counts": {
        "bookmarks": 0,
        "clients": 0,
        "followers": 6,
        "following": 9,
        "posts": 9,
        "users": 0
      },
      "follows_you": true,
      "you_blocked": false,
      "you_follow": true,
      "you_muted": false,
      "you_can_follow": true,
      "pagination_id": "1479179225"
    },
    {
      "id": "52",
      "created_at": "2016-10-12T14:19:46Z",
      "locale": "de",
      "timezone": "Europe/Zurich",
      "type": "human",
      "username": "papierzeit",
      "name": "Paper and Wizards",
      "content": {
        "html": "<span itemscope=\"https://pnut.io/schemas/Post\">The future belongs to paper and wizards.\r\nFaer&ucirc;n - Waterdeep</span>",
        "text": "The future belongs to paper and wizards.\r\nFaerûn - Waterdeep",
        "entities": {
          "links": [],
          "mentions": [],
          "tags": []
        },
        "avatar_image": {
          "height": 512,
          "width": 512,
          "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/DhZKgvJoi4QU0ML8KKnVLp4YyAhKH1miBwnW-E2AJsTx3lwOF_z7Nv8bCgn0pTCOVpAHPYvMHIs0c6pW_J359EBFJjTYD_NARrN1pr4YJrwy3WBvmnrEqvrxv9YIObwTrQ3iS__dFsPC",
          "is_default": false
        },
        "cover_image": {
          "height": 372,
          "width": 2560,
          "link": "https://d26y28lt6cxszo.cloudfront.net/cover/56baa644dcd4dde9cce4d12f5bbee160decfd0df160afc86136745346e517f8ab8f3a953bdd0b1a156e9f55e5f388528c5ddaf7a3023cf25fa2b6b53eb7926ed46999ecde304",
          "is_default": false
        }
      },
      "counts": {
        "bookmarks": 56,
        "clients": 0,
        "followers": 7,
        "following": 23,
        "posts": 102,
        "users": 0
      },
      "follows_you": true,
      "you_blocked": false,
      "you_follow": true,
      "you_muted": false,
      "you_can_follow": true,
      "pagination_id": "1479039055"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> follow</span><span class="method method-put">PUT</span> /users/<span class="call-param">{user_id}</span>/follow [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-users-id-follow) {#put-users-id-follow .endpoint}

Follow a user.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-3) {#url-parameters-3}

Name|Description
-|-
`user_id`|ID of the user to follow


##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/3/follow" \
    -X PUT \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns the followed user

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "3",
    "created_at": "2016-09-10T17:50:41Z",
    "locale": "en_US",
    "timezone": "America/Chicago",
    "type": "human",
    "username": "doctorlinguist",
    "content": {
      "avatar_image": {
        "is_default": true,
        "height": 512,
        "width": 512,
        "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/vFelanu1T4LVVWQ9RJDAjXm5hyuXlKaeXXCAzeig2e01v_d8qiv_AgYgfWkd2Oz0OUCLNn532ruc2_fSAxLVIJ3EO3BoPUgC37TIFxq1g7pk-oLTwmYhtsGNeaaO28vTRwpPyHK4BkOX"
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
      "clients": 1,
      "followers": 8,
      "following": 1,
      "posts": 1,
      "users": 0
    },
    "follows_you": true,
    "you_blocked": false,
    "you_follow": true,
    "you_muted": false,
    "you_can_follow": true
  }
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> follow</span><span class="method method-delete">DELETE</span> /users/<span class="call-param">{user_id}</span>/follow [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-users-id-follow) {#delete-users-id-follow .endpoint}

Unfollow a user.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-4) {#url-parameters-4}

Name|Description
-|-
`user_id`|ID of the user to unfollow

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/3/follow" \
    -X DELETE \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns the unfollowed user

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "3",
    "created_at": "2016-09-10T17:50:41Z",
    "locale": "en_US",
    "timezone": "America/Chicago",
    "type": "human",
    "username": "doctorlinguist",
    "content": {
      "avatar_image": {
        "is_default": true,
        "height": 512,
        "width": 512,
        "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/vFelanu1T4LVVWQ9RJDAjXm5hyuXlKaeXXCAzeig2e01v_d8qiv_AgYgfWkd2Oz0OUCLNn532ruc2_fSAxLVIJ3EO3BoPUgC37TIFxq1g7pk-oLTwmYhtsGNeaaO28vTRwpPyHK4BkOX"
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
      "clients": 1,
      "followers": 7,
      "following": 1,
      "posts": 1,
      "users": 0
    },
    "follows_you": true,
    "you_blocked": false,
    "you_follow": false,
    "you_muted": false,
    "you_can_follow": true
  }
}
```