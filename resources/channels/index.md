### Channels



##### Click For Example [<i class="fa fa-paragraph" aria-hidden="true"></i>](#channel) {#channel .endpoint}

```json
{
  "id": "5",
  "type": "io.pnut.33mhz",
  "owner": {
    "id": "1",
    "type": "human",
    "locale": "en_US",
    "timezone": "America/Chicago",
    "guid": "113BA773-F1F2-42CF-99F8-02EC778942C9",
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
  "recent_message_id": "16",
  "acl": {
    "full": {
      "immutable": true,
      "you": true,
      "user_ids": []
    },
    "write": {
      "any_user": true,
      "immutable": false,
      "you": true,
      "user_ids": []
    },
    "read": {
      "any_user": true,
      "immutable": false,
      "public": false,
      "you": true,
      "user_ids": []
    }
  },
  "counts": {
    "messages": 5,
    "subscribers": 1
  },
  "you_subscribed": true,
  "you_muted": false,
  "has_unread": true
}
```

#### Fields [<i class="fa fa-paragraph" aria-hidden="true"></i>](#channel-fields) {#channel-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
    </tr>

    <tr>
        <td><code>created_at</code></td>
        <td>string</td>
        <td>The time at which the channel was created in ISO 8601 format.</td>
    </tr>

    <tr>
        <td><code>id</code></td>
        <td>string</td>
        <td>Primary identifier for a channel. This will be an integer, but it is always expressed as a string to avoid limitations with the way JavaScript integers are expressed. This id space is unique to Channel objects. There can be a Post and User with the same ID; no relation is implied.</td>
    </tr>

    <tr>
        <td><code>is_active</code></td>
        <td>boolean</td>
        <td>Only included if <code>false</code>.</td>
    </tr>

    <tr>
        <td><code>type</code></td>
        <td>string</td>
        <td>The type of channel. Generally uses a reversed domain name to identify the intended purpose. None-core channel types (<code>io.pnut.core.*</code>) are not authenticated by the server; clients should not assume other clients created their channel types the same way.</td>
    </tr>

    <tr>
        <td><code>owner</code></td>
        <td>object</td>
        <td>This is an embedded <a href="https://pnut.io/docs/api/resources/user">User</a> object. Note: In certain cases (e.g., when a user account has been deleted), this key may be omitted.</td>
    </tr>

    <tr>
        <td><code>recent_message_id</code></td>
        <td>string</td>
        <td>Optional ID of the most recent message in the channel. Not included if no message has been created yet.</td>
    </tr>

    <tr>
        <td><code>recent_message</code></td>
        <td>object</td>
        <td>Optional embedded <a href="https://pnut.io/docs/api/resources/messages">Message</a> object.</td>
    </tr>

    <tr>
        <td><code>acl</code></td>
        <td>object</td>
        <td>
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>full</code></td>
                    <td>object</td>
                    <td>
                        <table>
                            <tr>
                                <th>Field</th>
                                <th>Type</th>
                                <th>Description</th>
                            </tr>

                            <tr>
                                <td><code>immutable</code></td>
                                <td>boolean</td>
                                <td>If full access is immutable.</td>
                            </tr>

                            <tr>
                                <td><code>you</code></td>
                                <td>boolean</td>
                                <td>If you have full access.</td>
                            </tr>

                            <tr>
                                <td><code>user_ids</code></td>
                                <td>list</td>
                                <td>A list of user IDs who have full access.</td>
                            </tr>
                        </table>
                    </td>
                </tr>

                <tr>
                    <td><code>write</code></td>
                    <td>object</td>
                    <td>
                        <table>
                            <tr>
                                <th>Field</th>
                                <th>Type</th>
                                <th>Description</th>
                            </tr>

                            <tr>
                                <td><code>any_user</code></td>
                                <td>boolean</td>
                                <td>Whether any user can write to the channel</td>
                            </tr>

                            <tr>
                                <td><code>immutable</code></td>
                                <td>boolean</td>
                                <td>If write access is immutable.</td>
                            </tr>

                            <tr>
                                <td><code>you</code></td>
                                <td>boolean</td>
                                <td>If you have write access.</td>
                            </tr>

                            <tr>
                                <td><code>user_ids</code></td>
                                <td>list</td>
                                <td>A list of user IDs who have write access.</td>
                            </tr>
                        </table>
                    </td>
                </tr>

                <tr>
                    <td><code>read</code></td>
                    <td>object</td>
                    <td>
                        <table>
                            <tr>
                                <th>Field</th>
                                <th>Type</th>
                                <th>Description</th>
                            </tr>

                            <tr>
                                <td><code>any_user</code></td>
                                <td>boolean</td>
                                <td>Whether any user can read the channel.</td>
                            </tr>

                            <tr>
                                <td><code>immutable</code></td>
                                <td>boolean</td>
                                <td>If read access is immutable.</td>
                            </tr>

                            <tr>
                                <td><code>public</code></td>
                                <td>boolean</td>
                                <td>If the channel can be read by unauthenticated access.</td>
                            </tr>

                            <tr>
                                <td><code>you</code></td>
                                <td>boolean</td>
                                <td>If you have read access.</td>
                            </tr>

                            <tr>
                                <td><code>user_ids</code></td>
                                <td>list</td>
                                <td>A list of user IDs who have read access.</td>
                            </tr>
                        </table>
                    </td>
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
                    <td><code>messages</code></td>
                    <td>integer</td>
                    <td>The number of messages in the channel.</td>
                </tr>

                <tr>
                    <td><code>subscribers</code></td>
                    <td>integer</td>
                    <td>Optional number of subscribers to the channel. Only included if the requesting user has <code>full</code> ACL access.</td>
                </tr>
            </table>
        </td>
    </tr>

    <tr>
        <td><code>you_subscribed</code></td>
        <td>boolean</td>
        <td>Whether or not you subscribe to the channel.</td>
    </tr>

    <tr>
        <td><code>you_muted</code></td>
        <td>boolean</td>
        <td>You muted subscriptions to the channel.</td>
    </tr>

    <tr>
        <td><code>has_unread</code></td>
        <td>boolean</td>
        <td>Your stream marker is not updated to the latest message in the channel.</td>
    </tr>
</table>


#### General Channel Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#general-channel-parameters) {#general-channel-parameters}

Any endpoint that returns channel objects can be subject to these parameters.

##### General Parameters

Name|Type|Description
-|-|-
`include_read`|integer (0 or 1)|Include channels that do not have unread messages. Defaults to true.
`channel_types`|string|Comma-separated list of channel types to retrieve. If not included, will return any channels the app is authorized to view.
`include_marker`|integer (0 or 1)|Include a [stream marker](stream-marker). Defaults to true except on `GET /channels/{channel_id}`
`include_inactive`|integer (0 or 1)|Include inactive channels. Defaults to false.
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects. Defaults to false.
`include_channel_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all channel objects. Defaults to false.
`include_recent_message`|integer (0 or 1)|Include the most recent message in the channel. Defaults to false.