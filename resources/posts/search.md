# Post Search

Endpoints:

* [Search posts](#get-posts-search)


## <span class="method method-get">GET</span> /posts/search {#get-posts-search .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of posts filtered by the given criteria.

### Query Parameters

#### Search

Name|Description
-|-
`q`|List of words included in posts

#### Sort

Name|Description
-|-
`order`|One of id or relevance. Default is by relevance

#### Filter

Name|Description
-|-
`client_id`|Only include posts created by this client ID
`created_after`|ISO 8601-formatted timestamp after which posts were created
`created_before`|ISO 8601-formatted timestamp before which posts were created
`creator_id`|Only include posts created by this user ID
`file_id`|Matches with this file attached
`file_kinds`|Comma-separated list of oEmbed-attached file types (`video`, `audio`, `image`, `other`)
`has_mentions`|`1` or `0` to include posts with or without mentions. Excludes other mentions filters below
`is_directed`|If `1`, only include [directed posts](../../implementation/entities#leading-mentions)
`is_nsfw`|If `0`, does not include NSFW posts
`is_reply`|`1` or `0` to include messages that are or are not replies
`is_revised`|If `1`, only include revised posts
`leading_mentions`|Comma-separated list of mentions at the beginning of a post. Any matches returned
`mentions`|Comma-separated list of mentions. Any matches returned
`poll_id`|Matches with this poll attached
`raw_types`|Comma-separated list of attached raw types. Any matches returned
`reply_to`|Only include posts replying to this post
`tags`|Comma-separated list of tags. Any matches returned
`thread_id`|Only include posts in this thread
`url_domains`|Comma-separated list of domains. Any matches returned. Do not include `http://` or `www` in front of domain
`urls`|Comma-separated list of URLs. Any matches returned
`user_types`|Comma-separated list of user types of: human, feed, bot

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/posts/search?tags=mndp,MondayNightDanceParty" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of posts

```json
{
    "meta": {
        "more": true,
        "max_id": "0",
        "min_id": "0",
        "code": 200
    },
    "data": [
        {"...Post Object..."},
        {"...Post Object..."}
    ]
}
```