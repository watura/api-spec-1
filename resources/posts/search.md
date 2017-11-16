### Post Search




#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /posts/search [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-posts-search) {#get-posts-search .endpoint}

Retrieve a list of posts filtered by the given criteria.

##### Query Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-parameters-1) {#query-parameters-1}

Name|Description
-|-
`order`|One of id or relevance. Default is by relevance
`q`|List of words included in posts
`tags`|Comma-separated list of tags. Any matches returned. Do not include `#`
`mentions`|Comma-separated list of mentions. Any matches returned. Do not include `@`
`leading_mentions`|Comma-separated list of mentions at the beginning of a post. Any matches returned. Do not include `@`
`links`|Comma-separated list of URLs. Any matches returned
`link_domains`|Comma-separated list of domains. Any matches returned. Do not include `http://` or `www` in front of domain
`is_directed`|If true, only include directed posts
`is_revised`|If true, only include revised posts
`is_nsfw`|If false, does not include NSFW posts
`is_reply`|If true, only include replies
`client_id`|Only include posts created by this client ID
`creator_id`|Only include posts created by this user ID
`reply_to`|Only include posts replying to this post
`thread_id`|Only include posts in this thread
`user_types`|Comma-separated list of user types of: human, feed, bot
`raw_types`|Comma-separated list of attached raw types. Any matches returned

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/posts/search?tags=mndp,MondayNightDanceParty" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of posts

```json

```