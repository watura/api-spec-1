# Polls


* [Poll Fields](#poll-fields)
* [General Poll Parameters](#general-poll-parameters)


## Poll Fields {#poll-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
    </tr>
    <tr>
        <td><code>closed_at</code></td>
        <td>string</td>
        <td>The time at which the poll closes in ISO 8601 format; YYYY-MM-DDTHH:MM:SSZ.</td>
    </tr>
    <tr>
        <td><code>created_at</code></td>
        <td>string</td>
        <td>The time at which the poll was created in ISO 8601 format; YYYY-MM-DDTHH:MM:SSZ.</td>
    </tr>
    <tr>
        <td><code>id</code></td>
        <td>string</td>
        <td>Primary identifier for a poll. This will be an integer, but it is always expressed as a string to avoid limitations with the way JavaScript integers are expressed. This id space is unique to poll objects. There can be a Post and Poll with the same ID; no relation is implied.</td>
    </tr>
    <tr>
        <td><code>is_anonymous</code></td>
        <td>boolean</td>
        <td>Whether poll results are anonymous, or if who responded to what option is displayed when the poll is over (or the creator of the poll looks at it).</td>
    </tr>
    <tr>
        <td><code>is_public</code></td>
        <td>boolean</td>
        <td>Whether poll is public or private. If private, it still may be attached to a public object, such as a post or a message.</td>
    </tr>
    <tr>
        <td><code>max_options</code></td>
        <td>integer</td>
        <td>How many options can be selected at once by responders. Default is <code>1</code>.</td>
    </tr>
    <tr>
        <td><code>options</code></td>
        <td>object</td>
        <td>A list of 2 to 10 responses for the poll.
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>
                <tr>
                    <td><code>text</code></td>
                    <td>string</td>
                    <td>Up to 64 Unicode characters. One response for users to choose for the poll. Any spaces, including line endings, will be replaced with a single space.</td>
                </tr>
                <tr>
                    <td><code>position</code></td>
                    <td>integer</td>
                    <td>Order of the option in the list of options, starting at <code>1</code> and going up sequentially. Assigned by the API if the user does not specify them.</td>
                </tr>
                <tr>
                    <td><code>is_your_response</code></td>
                    <td>boolean</td>
                    <td>True if user responded to the poll with this option.
                        <p class="text-explanation">Only set on authenticated user calls.</p></td>
                </tr>
                <tr>
                    <td><code>respondents</code></td>
                    <td>integer</td>
                    <td>Number of users that responded to the poll.
                        <p class="text-explanation">Only set if the poll is closed.</p></td>
                </tr>
                <tr>
                    <td><code>respondent_ids</code></td>
                    <td>object</td>
                    <td>A sample of respondent IDs.
                        <p class="text-explanation">Only set if <code>is_anonymous</code> is false and <code>respondents</code> is present.</p></td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>poll_token</code></td>
        <td>string</td>
        <td>A token to access and respond to the poll.
            <p class="text-explanation">Only set on <code>POST</code> creation response, if included in the query string, or if the Polls scope gives you access to the poll.</p></td>
    </tr>
    <tr>
        <td><code>prompt</code></td>
        <td>string</td>
        <td>A readable name of the poll. This is the prompt users will be responding to for the Options. Up to 256 Unicode characters. <em>Be sure to escape if necessary.</em></td>
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
                    <td>Description of the API consumer that created this poll.</td>
                </tr>
                <tr>
                    <td><code>id</code></td>
                    <td>string</td>
                    <td>The public client id of the API consumer that created this poll.</td>
                </tr>
                <tr>
                    <td><code>url</code></td>
                    <td>string</td>
                    <td>Link provided by the API consumer that created this poll.</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>string</td>
        <td>The type of poll. Generally uses a reversed domain name to identify the intended purpose. Non-core poll types (<code>io.pnut.core.*</code>) are not authenticated by the server; clients should not assume other clients created their poll types the same way.</td>
    </tr>
    <tr>
        <td><code>user</code></td>
        <td>object</td>
        <td>This is an embedded User object.
            <p class="text-explanation">In certain cases, this key may be omitted.</p></td>
    </tr>
    <tr>
        <td><code>user_id</code></td>
        <td>string</td>
        <td>Primary identifier for the user who created the poll.
            <p class="text-explanation">Only set if the <code>user</code> above is omitted.</p></td>
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
</table>


## General Poll Parameters {#general-poll-parameters}

Any endpoint that returns poll objects can be subject to these parameters.

### General Parameters

Name|Type|Description|Default
-|-|-
`include_closed`|integer (0 or 1)|Include closed polls. Only applicable to the user's poll stream.|true
`include_private`|integer (0 or 1)|Include private polls. Only applicable to the user's poll stream.|true
`poll_types`|string|Comma-separated list of poll types to retrieve. Only applicable to the user's poll stream. If not included, will return any polls the app is authorized to view.|all
`exclude_poll_types`|string|Comma-separated list of poll types not to retrieve. Only applicable to the user's poll stream. Ignored if `poll_types` set.|none
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects.|false
`include_poll_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all poll objects.|false
