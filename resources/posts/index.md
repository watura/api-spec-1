### Posts

#### Canonical Thread view

Posts can be viewed in their thread from `https://beta.pnut.io/@username/{post_id}`, and a short redirect via `https://posts.pnut.io/{post_id}`.


#### Object

##### Click For Example [<i class="fa fa-paragraph" aria-hidden="true"></i>](#post) {#post .endpoint}

```json
{
  "created_at": "2016-11-20T01:17:57Z",
  "id": "2301",
  "source": {
    "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
    "link": "http://xyz.s3rv.com",
    "name": "Broadsword"
  },
  "user": {
    "id": "9",
    "created_at": "2016-09-10T20:04:47Z",
    "locale": "en_US",
    "timezone": "America/Los_Angeles",
    "type": "human",
    "username": "thrrgilag",
    "name": "Morgan McMillian",
    "content": {
      "text": "I usually just make software work but on occasion I\'ll make actual software. Links to my various social profiles are found on my homepage.\r\n\r\nxmpp: thrrgilag@monkeystew.net",
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\">I usually just make software work but on occasion I&#039;ll make actual software. Links to my various social profiles are found on my homepage.\r\n\r\nxmpp: thrrgilag@monkeystew.net</span>",
      "entities": {
        "links": [],
        "mentions": [],
        "tags": []
      },
      "avatar_image": {
        "height": 178,
        "width": 178,
        "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/QRICId7zjKVkwFxlZYwW9ER_cLvoyx1uuZ_9lgQSoPcZDITkPTCAAzGcJRHt84WrdgowKjgLIsz7shHcQyktzKKaNsHHhBxhaW6n8UHIsyZqDPmM_ljj5hnkiOYGrNZS1ncbbJS0cjCz",
        "is_default": false
      },
      "cover_image": {
        "height": 223,
        "width": 960,
        "link": "https://d26y28lt6cxszo.cloudfront.net/cover/222edb68f1eba7502b81571e3fedf53f7e87261b816cdfc485c71630f26204c7775bb36cf62c5744eacf2d48a18c6f0e2cfe196b4e7977f618dc8c3f0e03ba5dc27fab42c9ee",
        "is_default": false
      }
    },
    "counts": {
      "bookmarks": 16,
      "clients": 4,
      "followers": 18,
      "following": 23,
      "posts": 399,
      "users": 0
    },
    "verified": {
      "domain": "monkeystew.org",
      "link": "https://monkeystew.org"
    },
    "follows_you": true,
    "you_blocked": false,
    "you_follow": false,
    "you_muted": false,
    "you_can_follow": true
  },
  "reply_to": "2300",
  "thread_id": "2297",
  "counts": {
    "bookmarks": 0,
    "reposts": 0,
    "replies": 1,
    "threads": 0
  },
  "content": {
    "text": "@33MHz hmmm, what if we just cut back on the pizza and just do beer?",
    "html": "<span itemscope=\"https://pnut.io/schemas/Post\"><span data-mention-id=\"1\" data-mention-name=\"33MHz\" itemprop=\"mention\">@33MHz</span> hmmm, what if we just cut back on the pizza and just do beer?</span>",
    "entities": {
      "links": [],
      "mentions": [
        {
          "id": "1",
          "len": 6,
          "pos": 0,
          "text": "33MHz",
          "is_leading": true
        }
      ],
      "tags": []
    }
  },
  "you_bookmarked": false,
  "you_reposted": false
}
```


#### Fields [<i class="fa fa-paragraph" aria-hidden="true"></i>](#post-fields) {#post-fields}

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
        <td>Only set if <code>true</code>.</td>
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
        <td>This is an embedded <a href="https://pnut.io/docs/api/resources/users">User</a> object. Note: In certain cases (e.g., when a user account has been deleted), this key may be omitted.</td>
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
        <td>string</td>
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
                    <td>Rich text information for this post. See the <a href="https://pnut.io/docs/api/implementation/entities">Entities</a> documentation.</td>
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



#### General Post Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#general-post-parameters) {#general-post-parameters}

Any endpoint that returns post objects can be subject to these parameters.

##### General Parameters

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
`include_copy_mentions`|integer (0 or 1)|Include "copy mentions" in the `/users/{user_id}/mentions` endpoint. Defaults to true.
`include_muted`|integer (0 or 1)|Include posts from users you have muted. Defaults to false.
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects. Defaults to false.
`include_post_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all post objects. Defaults to false.