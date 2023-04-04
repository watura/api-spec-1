# Channels


* [Channel Fields](#channel-fields)
* [General Channel Parameters](#general-channel-parameters)


## Channel Fields {#channel-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
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
                                <td>list of strings</td>
                                <td>A list of user IDs who have full access.</td>
                            </tr>
                            <tr>
                                <td><code>users</code></td>
                                <td>list of objects</td>
                                <td>A list of user objects.
                                    <p class="text-explanation">Only set when <code>include_limited_users</code> is true.</p></td>
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
                                <td>list of strings</td>
                                <td>A list of user IDs who have write access.</td>
                            </tr>
                            <tr>
                                <td><code>users</code></td>
                                <td>list of objects</td>
                                <td>A list of user objects.
                                    <p class="text-explanation">Only set when <code>include_limited_users</code> is true.</p></td>
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
                                <td>list of strings</td>
                                <td>A list of user IDs who have read access.</td>
                            </tr>
                            <tr>
                                <td><code>users</code></td>
                                <td>list of objects</td>
                                <td>A list of user objects.
                                    <p class="text-explanation">Only set when <code>include_limited_users</code> is true.</p></td>
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
                    <td>The number of subscribers to the channel.
                        <p class="text-explanation">Only set if the requesting user has <code>full</code> ACL access.</p></td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>created_at</code></td>
        <td>string</td>
        <td><p>The time at which the channel was created in ISO 8601 format; YYYY-MM-DDTHH:MM:SSZ.</p>
            <p class="text-explanation">Added at the end of 2020, in version 1.0.0. Channels created before then have it set to the earliest message in the channel.</p></td>
    </tr>
    <tr>
        <td><code>has_sticky_messages</code></td>
        <td>boolean</td>
        <td>The channel contains sticky messages.</td>
    </tr>
    <tr>
        <td><code>has_unread</code></td>
        <td>boolean</td>
        <td>Your stream marker is not updated to the latest message in the channel.
            <p class="text-explanation">Only set if the call is authenticated.</p></td>
    </tr>
    <tr>
        <td><code>id</code></td>
        <td>string</td>
        <td>Primary identifier for a channel. This will be an integer, but it is always expressed as a string to avoid limitations with the way JavaScript integers are expressed. This id space is unique to Channel objects. There can be a Post and User with the same ID; no relation is implied.</td>
    </tr>
    <tr>
        <td><code>is_active</code></td>
        <td>boolean</td>
        <td>Whether the channel is archival or still usable.
            <p class="text-explanation">Only set if <code>false</code>.</p></td>
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
        <td><code>recent_deleted_message</code></td>
        <td>object</td>
        <td>Embedded <a href="messages">Message</a> object of the <code>recent_deleted_message_id</code>.
            <p class="text-explanation">Only set if <code>include_recent_message</code> is true and the most recent message is a deleted message.</p></td>
    </tr>
    <tr>
        <td><code>recent_deleted_message_id</code></td>
        <td>string</td>
        <td>ID of the most recent message <em>that has been deleted</em> in the channel.
            <p class="text-explanation">Only set if the most recent message in a channel is a deleted message.</p></td>
    </tr>
    <tr>
        <td><code>recent_message</code></td>
        <td>object</td>
        <td>Embedded <a href="messages">Message</a> object of the <code>recent_message_id</code>.
            <p class="text-explanation">Only set if <code>include_recent_message</code> is true.</p></td>
    </tr>
    <tr>
        <td><code>recent_message_id</code></td>
        <td>string</td>
        <td>ID of the most recent message in the channel. Ignores deleted messages.
            <p class="text-explanation">Not set if no message has been created yet or only deleted messages are in the channel.</p></td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>string</td>
        <td>The type of channel. Generally uses a reversed domain name to identify the intended purpose. None-core channel types (<code>io.pnut.core.*</code>) are not authenticated by the server; clients should not assume other clients created a custom channel type the same way.</td>
    </tr>
    <tr>
        <td><code>you_muted</code></td>
        <td>boolean</td>
        <td>You muted subscriptions to the channel.
            <p class="text-explanation">Only set on authenticated calls.</p></td>
    </tr>
    <tr>
        <td><code>you_subscribed</code></td>
        <td>boolean</td>
        <td>Whether or not you subscribe to the channel.
            <p class="text-explanation">Only set on authenticated calls.</p></td>
    </tr>
    <tr>
        <td><code>user</code></td>
        <td>object</td>
        <td>This is an embedded object of the <a href="users">User</a> that owns the channel.
            <p class="text-explanation">In certain cases (e.g., when a user account has been deleted), this may be omitted. In that case, <code>user_id</code> will still be set. <a href="../how-to/private-messages">Private messages are an exception</a>.</p></td>
    </tr>
    <tr>
        <td><code>user_id</code></td>
        <td>string</td>
        <td>Primary identifier for the user who created the channel.
            <p class="text-explanation">This is only set if the <code>user</code> above is omitted.</p></td>
    </tr>
</table>


## General Channel Parameters {#general-channel-parameters}

Any endpoint that returns channel objects can be subject to these parameters.

### General Parameters

Name|Type|Description|Default
-|-|-|-
`include_read`|integer (0 or 1)|Include channels that do not have unread messages.|true
`channel_types`|string|Comma-separated list of channel types to retrieve. If not included, will return any channels the app is authorized to view.|all
`exclude_channel_types`|string|Comma-separated list of channel types *not* to retrieve. If `channel_types` is set, this is ignored.|none
`include_marker`|integer (0 or 1)|Include a [stream marker](stream-marker).|true except on `GET /channels/{channel_id}`
`include_inactive`|integer (0 or 1)|Include inactive channels.|false
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects.|false
`include_channel_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all channel objects.|false
`include_recent_message`|integer (0 or 1)|Include the most recent message in the channel (and the recent deleted message, if the most recent message was deleted).|false
`include_limited_users`|integer (0 or 1)|Include limited user objects in the ACL. Only on `/users/me/channels/subscribed` and `/channels/{channel_id}`. User objects include `username`, `id`, `name` (if set), `avatar_image` (as URL only), and `presence` (if not offline).|false
