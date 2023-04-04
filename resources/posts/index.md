# Posts

* [Canonical Thread view](#canonical-thread-view)
* [Post Fields](#post-fields)
* [General Post Parameters](#general-post-parameters)

## Canonical Thread view {#canonical-thread-view}

Posts can be viewed in their thread via a short redirect at `https://posts.pnut.io/{post_id}`.


## Post Fields {#post-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
    </tr>
    <tr>
        <td><code>bookmarked_by</code></td>
        <td>list of objects</td>
        <td>A sampled list of Users who bookmarked the post.
        <p class="text-explanation">Only set if query parameter <code>include_bookmarked_by</code> specified.</p></td>
    </tr>
    <tr>
        <td><code>content</code></td>
        <td>object</td>
        <td>
            <p class="text-explanation">Not set if the post has been deleted.</p>
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>
                <tr>
                    <td><code>entities</code></td>
                    <td>object</td>
                    <td>Rich text information for this post. See the <a href="../implementation/entities">Entities</a> documentation.</td>
                </tr>
                <tr>
                    <td><code>html</code></td>
                    <td>string</td>
                    <td>Server-generated annotated HTML rendering of post text.</td>
                </tr>
                <tr>
                    <td><code>text</code></td>
                    <td>string</td>
                    <td>User supplied text of the post. All Unicode characters allowed. Maximum length 256 characters. The maximum length can be retrieved from the Configuration endpoint.</td>
                </tr>
            </table>
        </td>
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
        <td><code>created_at</code></td>
        <td>string</td>
        <td>The time at which the post was created in ISO 8601 format; YYYY-MM-DDTHH:MM:SSZ.</td>
    </tr>
    <tr>
        <td><code>id</code></td>
        <td>string</td>
        <td>Primary identifier for a post. This will be an integer, but it is always expressed as a string to avoid limitations with the way JavaScript integers are expressed. This id space is unique to Post objects. There can be a Post and User with the same ID; no relation is implied.</td>
    </tr>
    <tr>
        <td><code>is_deleted</code></td>
        <td>boolean</td>
        <td>Post is deleted. <code>content</code> will not be set.
            <p class="text-explanation">Only set if <code>true</code>.</p></td>
    </tr>
    <tr>
        <td><code>is_nsfw</code></td>
        <td>boolean</td>
        <td>User marked the post as "Not Safe For Work".
        <p class="text-explanation">Only set if <code>true</code>.</p></td>
    </tr>
    <tr>
        <td><code>is_revised</code></td>
        <td>boolean</td>
        <td>Post has been revised. Looking up the revised posts will return a result.
        <p class="text-explanation">Only set if <code>true</code>.</p></td>
    </tr>
    <tr>
        <td><code>raw</code></td>
        <td>object</td>
        <td>The raw items attached to this object.
            <p class="text-explanation">Only set if query parameter specified.</p>
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>
                <tr>
                    <td><code>{type name}</code></td>
                    <td>list of objects</td>
                    <td>A list of objects of this type.</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>reply_to</code></td>
        <td>string</td>
        <td>ID of the post this post is replying to.
            <p class="text-explanation">Only set if a reply.</p></td>
    </tr>
    <tr>
        <td><code>repost_of</code></td>
        <td>object</td>
        <td>Embedded post object being reposted.
            <p class="text-explanation">Only set if a repost of another post.</p></td>
    </tr>
    <tr>
        <td><code>reposted_by</code></td>
        <td>list of objects</td>
        <td>A sampled list of users who reposted the post.
            <p class="text-explanation">Only set if query parameter <code>include_bookmarked_by</code> specified.</p></td>
    </tr>
    <tr>
        <td><code>revision</code></td>
        <td>integer</td>
        <td>Revision number of the post.
            <p class="text-explanation">Only set if post is a "previous" version of a post. (i.e., from the <a href="posts/lookup#get-posts-id-revisions"><code>/posts/{post_id}/revisions</code></a> endpoint).</p></td>
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
                    <td><code>id</code></td>
                    <td>string</td>
                    <td>The public client ID of the API consumer ("app") that created this post.</td>
                </tr>
                <tr>
                    <td><code>name</code></td>
                    <td>string</td>
                    <td>Description of the API consumer that created this post.</td>
                </tr>
                <tr>
                    <td><code>url</code></td>
                    <td>string</td>
                    <td>Link provided by the API consumer that created this post.</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>thread_id</code></td>
        <td>string</td>
        <td>The ID of the post at the root of the thread that this post is a part of. If <code>thread_id==id</code> then this property does not guarantee that the thread has > 1 post. Please see <code>replies</code> count.</td>
    </tr>
    <tr>
        <td><code>user</code></td>
        <td>object</td>
        <td>This is an embedded object of the <a href="users">User</a> that created the post.
            <p class="text-explanation">In certain cases (e.g., when the user account has been deleted), this key may be omitted.</p></td>
    </tr>
    <tr>
        <td><code>user_id</code></td>
        <td>string</td>
        <td>Primary identifier for the user who created the channel.
            <p class="text-explanation">Only set if the <code>user</code> above is omitted.</p></td>
    </tr>
    <tr>
        <td><code>you_bookmarked</code></td>
        <td>boolean</td>
        <td>True if authenticated user bookmarked the post.
            <p class="text-explanation">Only set on authenticated calls.</p></td>
    </tr>
    <tr>
        <td><code>you_reposted</code></td>
        <td>boolean</td>
        <td>True if authenticated user reposted the post.
            <p class="text-explanation">Only set on authenticated calls.</p></td>
    </tr>
</table>



## General Post Parameters {#general-post-parameters}

Any endpoint that returns post objects can be subject to these parameters.

### General Parameters

Name|Type|Description|Default
-|-|-|-
`include_deleted`|integer (0 or 1)|Include deleted posts.|true
`include_client`|integer (0 or 1)|Include the client object with the post. If false, `source` will be the client ID string instead of the client object.|true
`include_counts`|integer (0 or 1)|Include the post's counts. Also affects any included user object.|true
`include_html`|integer (0 or 1)|Should the post and user `html` field be included alongside the `text` field in the response objects?|true
`include_post_html`|integer (0 or 1)|Should the post `html` field be included alongside the `text` field in the response objects?|true. `include_html` takes priority if present.
`include_bookmarked_by`|integer (0 or 1)|Include `bookmarked_by`: a sampled list of users who bookmarked the post.|false
`include_reposted_by`|integer (0 or 1)|Include `reposted_by`: a sampled list of users who reposted the post.|false
`include_directed_posts`|integer (0 or 1)|Include posts with "leading mentions" of users you do not follow. Not applicable to all post streams.|true
`include_mention_posts`|integer (0 or 1)|Include posts with mentions.|true
`include_copy_mentions`|integer (0 or 1)|Include "copy mentions" in the `/users/{user_id}/mentions` endpoint.|true
`include_replies`|integer (0 or 1)|Include posts replying to other posts.|true
`include_muted`|integer (0 or 1)|Include posts from users you have muted.|false
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects.|false
`include_post_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all post objects.|false
