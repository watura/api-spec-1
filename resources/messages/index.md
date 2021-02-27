# Messages


* [Message Fields](#message-fields)
* [General Poll Parameters](#general-poll-parameters)


## Message Fields {#message-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
    </tr>
    <tr>
        <td><code>channel_id</code></td>
        <td>string</td>
        <td>Primary identifier for the channel this message is a part of. This will be an integer, but it is always expressed as a string to avoid limitations with the way JavaScript integers are expressed. This id space is unique to Channel objects.</td>
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
                    <td><code>replies</code></td>
                    <td>integer</td>
                    <td>The number of messages created in reply to this message.</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>created_at</code></td>
        <td>string</td>
        <td>The time at which the message was created in ISO 8601 format; YYYY-MM-DDTHH:MM:SSZ.</td>
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
                    <td><code>id</code></td>
                    <td>string</td>
                    <td>The public client id of the API consumer that created this message.</td>
                </tr>
                <tr>
                    <td><code>url</code></td>
                    <td>string</td>
                    <td>Link provided by the API consumer that created this message.</td>
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
        <td>This is an embedded <a href="users">User</a> object. Note: In certain cases (e.g., when a user account has been deleted), this key may be omitted.</td>
    </tr>
    <tr>
        <td><code>user_id</code></td>
        <td>string</td>
        <td>Primary identifier for the user who created the message. This is only included if the <code>user</code> above is omitted.</td>
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
                    <td>Rich text information for this message. See <a href="../implementation/entities">Entities</a>.</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>raw</code></td>
        <td>object</td>
        <td>The raw items attached to this object. Only included if query parameter specified.
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>
                <tr>
                    <td><code>{type name}</code></td>
                    <td>list</td>
                    <td>A list of objects of this type.</td>
                </tr>
            </table>
        </td>
    </tr>
</table>


## General Message Parameters {#general-message-parameters}

Any endpoint that returns message objects can be subject to these parameters.

### General Parameters

Name|Type|Description
-|-|-
`include_deleted`|integer (0 or 1)|Include deleted messages. Defaults to true.
`include_html`|integer (0 or 1)|Should the message and user `html` field be included alongside the `text` field in the response objects? Defaults to true.
`include_message_html`|integer (0 or 1)|Should the message `html` field be included alongside the `text` field in the response objects? Defaults to true. Note that `include_html` takes priority if present.
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects. Defaults to false.
`include_message_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all message objects. Defaults to false.
`include_client`|integer (0 or 1)|Include the client object with the post. Defaults to true.