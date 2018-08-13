# Channels


## Object

[Use live API calls for an example of the object.](/docs/api/resources/channels/lookup#get-channels-id)


## Fields [&para;](#channel-fields) {#channel-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
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
        <td>This is an embedded <a href="users">User</a> object. Note: In certain cases (e.g., when a user account has been deleted), this key may be omitted.</td>
    </tr>

    <tr>
        <td><code>recent_message_id</code></td>
        <td>string</td>
        <td>Optional ID of the most recent message in the channel. Not included if no message has been created yet.</td>
    </tr>

    <tr>
        <td><code>recent_message</code></td>
        <td>object</td>
        <td>Optional embedded <a href="messages">Message</a> object.</td>
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
                                <td>A list of user IDs who have full access. (or a list of objects, in certain cases)</td>
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
                                <td>A list of user IDs who have write access. (or a list of objects, in certain cases)</td>
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
                                <td>A list of user IDs who have read access. (or a list of objects, in certain cases)</td>
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


## General Channel Parameters [&para;](#general-channel-parameters) {#general-channel-parameters}

Any endpoint that returns channel objects can be subject to these parameters.

### General Parameters

Name|Type|Description
-|-|-
`include_read`|integer (0 or 1)|Include channels that do not have unread messages. Defaults to true.
`channel_types`|string|Comma-separated list of channel types to retrieve. If not included, will return any channels the app is authorized to view.
`exclude_channel_types`|string|Comma-separated list of channel types *not* to retrieve. If `channel_types` is set, this is ignored.
`include_marker`|integer (0 or 1)|Include a [stream marker](stream-marker). Defaults to true except on `GET /channels/{channel_id}`
`include_inactive`|integer (0 or 1)|Include inactive channels. Defaults to false.
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects. Defaults to false.
`include_channel_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all channel objects. Defaults to false.
`include_recent_message`|integer (0 or 1)|Include the most recent message in the channel. Defaults to false.
`include_limited_users`|integer (0 or 1)|Include limited user objects instead of user IDs in the ACL. Only on `/users/me/channels/subscribed` and `/channels/{channel_id}`. User objects include `username`, `id`, `name` (if set), `avatar_image` (as URL only), and `presence` (if not offline). Defaults to false.