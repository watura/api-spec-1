# Reposts

Endpoints:

* [Create a Repost](#put-posts-id-repost)
* [Delete a repost](#delete-posts-id-repost)

Reposts are special posts. You cannot reply to, repost, or bookmark a repost, but the API will instead reply to, repost, or bookmark the original post that was reposted.

Even if a post is revised, existing reposts will still reflect the acted-on post's original contents, not the revision.

__Contents__

Reposts act as complete posts in themselves, with the "original" post embedded as an additional object in the `repost_of` field. The `contents`, `counts`, `raw`, `is_revised`, and `is_nsfw` fields of the post will mirror the acted-on post.

__Deletion__

When a repost is deleted, it will henceforth return a `404 Not Found`, instead of returning a normal post with `is_deleted: true`. When the acted-on post is deleted, all reposts of it will also be deleted.

__Return Values__

When creating or deleting a repost, the API returns the acted-on post, not the newly created post. This is the same as when bookmarking a post.


## <span class="method method-put">PUT</span> /posts/<span class="call-param">{post_id}</span>/repost {#put-posts-id-repost .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">write_post</span>

Repost another post. The repost will show up in followers' streams if they have not seen another repost of the same within the last week, and if the reposted post is not in their recent stream. It is created in its own thread, not the thread of the original post. This increments a user's post count.

Reposts can be marked as NSFW just like a normal post, but will always identify as NSFW if the embedded original post was marked as NSFW. The "repost" will be marked NSFW, but the embedded original post will be embedded however it was created. So a client can see that difference if it is useful.

### URL Parameters

Name|Description
-|-
`post_id`|ID of the post to repost

### POST Body Data

Name|Description
-|-
`is_nsfw`|If true, the post will be marked as "NSFW" (Not Safe For Work/mature/offensive).

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/posts/2370/repost" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the original post that has been reposted.

```json
{
    "meta": {
        "code": 201
    },
    "data": {"...Post object..."}
}
```


## <span class="method method-delete">DELETE</span> /posts/<span class="call-param">{post_id}</span>/repost {#delete-posts-id-repost .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">write_post</span>

Delete a repost. The actual repost is completely deleted; it does not leave behind a thread or deleted post to look up.

Users can also delete their own reposts even if they no longer have access to the original reposted post (e.g., they were blocked). In that case, the returned post in the `data` field is simply `{"id":POST_ID,"you_reposted":false}`.

### URL Parameters

Name|Description
-|-
`post_id`|ID of the post to delete a repost for

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/posts/2370/repost" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the original post that was previously reposted.

```json
{
    "meta": {
        "code": 200
    },
    "data": {"....Post object..."}
}
```
