# Posts

## Canonical Thread view

Posts can be viewed in their thread via a short redirect at `https://posts.pnut.io/{post_id}`.


## Object

[Use live API calls for an example of the object.](/docs/api/resources/posts/lookup#get-posts-id)


## Fields {#post-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
    </tr>

    <tr>
        <td><code>created_at</code></td>
        <td>string</td>
        <td>The time at which the post was created in ISO 8601 format.</td>
    </tr>

    <tr>
        <td><code>id</code></td>
        <td>string</td>
        <td>Primary identifier for a post. This will be an integer, but it is always expressed as a string to avoid limitations with the way JavaScript integers are expressed. This id space is unique to Post objects. There can be a Post and User with the same ID; no relation is implied.</td>
    </tr>

    <tr>
        <td><code>is_deleted</code></td>
        <td>boolean</td>
        <td>Only set if <code>true</code>. Post is deleted. `content` will not be set.</td>
    </tr>

    <tr>
        <td><code>is_nsfw</code></td>
        <td>boolean</td>
        <td>Only set if <code>true</code>. User marked the post as "Not Safe For Work".</td>
    </tr>

    <tr>
        <td><code>is_revised</code></td>
        <td>boolean</td>
        <td>Only set if <code>true</code>. Post has been revised. Looking up the revised posts will return a result.</td>
    </tr>

    <tr>
        <td><code>revision</code></td>
        <td>string</td>
        <td>Only set if post is a "previous" version of a post. (i.e., from the <a href="posts/lookup#get-posts-id-revisions"><code>/posts/{post_id}/revisions</code></a> endpoint).</td>
    </tr>

    <tr>
        <td><code>source</code></td>
        <td>object</td>
        <td>
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>name</code></td>
                    <td>string</td>
                    <td>Description of the API consumer that created this post.</td>
                </tr>

                <tr>
                    <td><code>link</code></td>
                    <td>string</td>
                    <td>Link provided by the API consumer that created this post.</td>
                </tr>

                <tr>
                    <td><code>id</code></td>
                    <td>string</td>
                    <td>The public client id of the API consumer ("app") that created this post.</td>
                </tr>
            </table>
        </td>
    </tr>

    <tr>
        <td><code>user</code></td>
        <td>object</td>
        <td>This is an embedded <a href="users">User</a> object. Note: In certain cases (e.g., when a user account has been deleted), this key may be omitted.</td>
    </tr>

    <tr>
        <td><code>thread_id</code></td>
        <td>string</td>
        <td>The id of the post at the root of the thread that this post is a part of. If <code>thread_id==id</code> then this property does not guarantee that the thread has > 1 post. Please see <code>replies</code> count.</td>
    </tr>

    <tr>
        <td><code>reply_to</code></td>
        <td>string</td>
        <td>Optional id of the post this post is replying to.</td>
    </tr>

    <tr>
        <td><code>repost_of</code></td>
        <td>object</td>
        <td>Optional embedded post object being reposted.</td>
    </tr>

    <tr>
        <td><code>counts</code></td>
        <td>object</td>
        <td>
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>bookmarks</code></td>
                    <td>integer</td>
                    <td>The number of users who have bookmarked this post.</td>
                </tr>

                <tr>
                    <td><code>replies</code></td>
                    <td>integer</td>
                    <td>The number of posts created in reply to this post.</td>
                </tr>

                <tr>
                    <td><code>reposts</code></td>
                    <td>integer</td>
                    <td>The number of users who have reposted this post.</td>
                </tr>

                <tr>
                    <td><code>threads</code></td>
                    <td>integer</td>
                    <td>The number of threads created in reply to this or other children of this post.</td>
                </tr>
            </table>
        </td>
    </tr>

    <tr>
        <td><code>content</code></td>
        <td>object</td>
        <td>
            <p class="text-explanation">NOTE: Not included if the post has been deleted.</p>

            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>text</code></td>
                    <td>string</td>
                    <td>User supplied text of the post. All Unicode characters allowed. Maximum length 256 characters. The maximum length can be retrieved from the Configuration endpoint.</td>
                </tr>

                <tr>
                    <td><code>html</code></td>
                    <td>string</td>
                    <td>Server-generated annotated HTML rendering of post text.</td>
                </tr>

                <tr>
                    <td><code>entities</code></td>
                    <td>object</td>
                    <td>Rich text information for this post. See the <a href="../implementation/entities">Entities</a> documentation.</td>
                </tr>

                <tr>
                    <td><code>links_not_parsed</code></td>
                    <td>boolean</td>
                    <td>If set, the server has not yet attempted to retrieve a title and description for link entities in this post.</td>
                </tr>
            </table>
        </td>
    </tr>

    <tr>
        <td><code>you_bookmarked</code></td>
        <td>boolean</td>
        <td>(Optional) True if authenticated user bookmarked the post</td>
    </tr>

    <tr>
        <td><code>you_reposted</code></td>
        <td>boolean</td>
        <td>(Optional) True if authenticated user reposted the post</td>
    </tr>
</table>



## General Post Parameters {#general-post-parameters}

Any endpoint that returns post objects can be subject to these parameters.

### General Parameters

Name|Type|Description
-|-|-
`include_deleted`|integer (0 or 1)|Include deleted posts. Defaults to true.
`include_client`|integer (0 or 1)|Include the client object with the post. Defaults to true.
`include_counts`|integer (0 or 1)|Include the post's counts. Also affects any included user object. Defaults to true.
`include_html`|integer (0 or 1)|Should the post and user `html` field be included alongside the `text` field in the response objects? Defaults to true.
`include_post_html`|integer (0 or 1)|Should the post `html` field be included alongside the `text` field in the response objects? Defaults to true. Note that `include_html` takes priority if present.
`include_bookmarked_by`|integer (0 or 1)|Include `bookmarked_by`: a sampled list of users who bookmarked the post. Defaults to false.
`include_reposted_by`|integer (0 or 1)|Include `reposted_by`: a sampled list of users who reposted the post. Defaults to false.
`include_directed_posts`|integer (0 or 1)|Include posts with "leading mentions" of users you do not follow. Not applicable to all post streams. Defaults to true.
`include_mention_posts`|integer (0 or 1)|If false, do not include posts with mentions
`include_copy_mentions`|integer (0 or 1)|Include "copy mentions" in the `/users/{user_id}/mentions` endpoint. Defaults to true.
`include_replies`|integer (0 or 1)|If false, do not include posts replying to other posts
`include_muted`|integer (0 or 1)|Include posts from users you have muted. Defaults to false.
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects. Defaults to false.
`include_post_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all post objects. Defaults to false.