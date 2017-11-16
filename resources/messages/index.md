### Messages


#### Object

##### Click For Example [<i class="fa fa-paragraph" aria-hidden="true"></i>](#message) {#message .endpoint}

```json
{
  "id": "16",
  "channel_id": "5",
  "created_at": "2017-01-04T01:51:40Z",
  "source": {
    "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
    "link": "http://xyz.s3rv.com",
    "name": "Broadsword"
  },
  "reply_to": "13",
  "thread_id": "13",
  "user": {
    "id": "1",
    "type": "human",
    "locale": "en_US",
    "timezone": "America/Chicago",
    "created_at": "2016-09-09T17:16:39Z",
    "username": "33MHz",
    "name": "Robert",
    "content": {
      "text": "Good times and great oldies!",
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\">Good times and great oldies!</span>",
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
      "posts": 924,
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
  },
  "content": {
    "html": "<span itemscope=\"https://pnut.io/schemas/Post\">test 2</span>",
    "text": "test 2",
    "entities": {
      "mentions": [],
      "links": [],
      "tags": []
    }
  }
}
```

#### Fields [<i class="fa fa-paragraph" aria-hidden="true"></i>](#message-fields) {#message-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
    </tr>

    <tr>
        <td><code>created_at</code></td>
        <td>string</td>
        <td>The time at which the message was created in ISO 8601 format.</td>
    </tr>

    <tr>
        <td><code>id</code></td>
        <td>string</td>
        <td>Primary identifier for a message. This will be an integer, but it is always expressed as a string to avoid limitations with the way JavaScript integers are expressed. This id space is unique to Message objects. There can be a Post and User with the same ID; no relation is implied.</td>
    </tr>

    <tr>
        <td><code>is_deleted</code></td>
        <td>boolean</td>
        <td>Only set if <code>true</code>.</td>
    </tr>

    <tr>
        <td><code>is_sticky</code></td>
        <td>boolean</td>
        <td>Whether a <code>full</code>-access user has stickied the message.</td>
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
                    <td>Description of the API consumer that created this message.</td>
                </tr>

                <tr>
                    <td><code>link</code></td>
                    <td>string</td>
                    <td>Link provided by the API consumer that created this message.</td>
                </tr>

                <tr>
                    <td><code>id</code></td>
                    <td>string</td>
                    <td>The public client id of the API consumer that created this message.</td>
                </tr>
            </table>
        </td>
    </tr>

    <tr>
        <td><code>reply_to</code></td>
        <td>string</td>
        <td>Optional id of the message this message is replying to.</td>
    </tr>

    <tr>
        <td><code>thread_id</code></td>
        <td>string</td>
        <td>The id of the message at the root of the thread that this message is a part of. If <code>thread_id==id</code> then this property does not guarantee that the thread has > 1 message.</td>
    </tr>

    <tr>
        <td><code>user</code></td>
        <td>object</td>
        <td>This is an embedded <a href="https://pnut.io/docs/api/resources/user">User</a> object. Note: In certain cases (e.g., when a user account has been deleted), this key may be omitted.</td>
    </tr>

    <tr>
        <td><code>content</code></td>
        <td>object</td>
        <td>
            <p class="text-explanation">NOTE: Not included if the message has been deleted.</p>

            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>text</code></td>
                    <td>string</td>
                    <td>User supplied text of the message. All Unicode characters allowed. Maximum length 2048 characters. The maximum length can be retrieved from the Configuration endpoint.</td>
                </tr>

                <tr>
                    <td><code>html</code></td>
                    <td>string</td>
                    <td>Server-generated annotated HTML rendering of message text.</td>
                </tr>

                <tr>
                    <td><code>entities</code></td>
                    <td>object</td>
                    <td>Rich text information for this message. See the <a href="https://pnut.io/docs/api/implementation/entities">Entities documentation.</td>
                </tr>
            </table>
        </td>
    </tr>
</table>


#### General Message Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#general-message-parameters) {#general-message-parameters}

Any endpoint that returns message objects can be subject to these parameters.

##### General Parameters

Name|Type|Description
-|-|-
`include_deleted`|integer (0 or 1)|Include deleted messages. Defaults to true.
`include_html`|integer (0 or 1)|Should the message and user `html` field be included alongside the `text` field in the response objects? Defaults to true.
`include_message_html`|integer (0 or 1)|Should the message `html` field be included alongside the `text` field in the response objects? Defaults to true. Note that `include_html` takes priority if present.
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects. Defaults to false.
`include_message_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all message objects. Defaults to false.
`include_client`|integer (0 or 1)|Include the client object with the post. Defaults to true.