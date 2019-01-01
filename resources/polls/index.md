# Polls


## Object

[Use live API calls for an example of the object.](/docs/api/resources/polls/lookup#get-polls-id)


## Fields {#poll-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
    </tr>

    <tr>
        <td><code>closed_at</code></td>
        <td>string</td>
        <td>The time at which the poll closes in ISO 8601 format.</td>
    </tr>

    <tr>
        <td><code>created_at</code></td>
        <td>string</td>
        <td>The time at which the poll was created in ISO 8601 format.</td>
    </tr>

    <tr>
        <td><code>id</code></td>
        <td>string</td>
        <td>Primary identifier for a poll. This will be an integer, but it is always expressed as a string to avoid limitations with the way JavaScript integers are expressed. This id space is unique to poll objects. There can be a Post and User with the same ID; no relation is implied.</td>
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
                    <td>Optional. Present if authenticated as a user. True if user responded to the poll with this option.</td>
                </tr>

                <tr>
                    <td><code>respondents</code></td>
                    <td>integer</td>
                    <td>Optional. Present if authenticated user a) created the poll, b) has responded to the poll, or c) the poll is closed.</td>
                </tr>

                <tr>
                    <td><code>respondent_ids</code></td>
                    <td>object</td>
                    <td>Optional. Present if <code>is_anonymous</code> is <code>false</code> and a condition for <code>respondents</code> above is also met.</td>
                </tr>
            </table>
        </td>
    </tr>

    <tr>
        <td><code>poll_token</code></td>
        <td>string</td>
        <td>A token to access and respond to the poll. Only included on creation, if included in the query string, or if the Polls scope gives you access to the poll.</td>
    </tr>

    <tr>
        <td><code>prompt</code></td>
        <td>string</td>
        <td>A readable name of the poll. This is the prompt users will be responding to for the Options. Up to 256 Unicode characters. <em>Be sure to escape if necessary.</em></td>
    </tr>

    <tr>
        <td><code>source</code></td>
        <td>object</td>
        <td>An embedded object of the client that created the poll.</td>
    </tr>

    <tr>
        <td><code>type</code></td>
        <td>string</td>
        <td>The type of poll. Generally uses a reversed domain name to identify the intended purpose. Non-core poll types (<code>io.pnut.core.*</code>) are not authenticated by the server; clients should not assume other clients created their poll types the same way.</td>
    </tr>

    <tr>
        <td><code>user</code></td>
        <td>object</td>
        <td>This is an embedded User object. In certain cases, this key may be omitted.</td>
    </tr>
</table>


## General Poll Parameters {#general-poll-parameters}

Any endpoint that returns poll objects can be subject to these parameters.

### General Parameters

Name|Type|Description
-|-|-
`include_closed`|integer (0 or 1)|Include closed polls. Only applicable to the user's poll stream. Defaults to true.
`include_private`|integer (0 or 1)|Include private polls. Only applicable to the user's poll stream. Defaults to true.
`poll_types`|string|Comma-separated list of poll types to retrieve. Only applicable to the user's poll stream. If not included, will return any polls the app is authorized to view.
`exclude_poll_types`|string|Comma-separated list of poll types not to retrieve. Only applicable to the user's poll stream. Ignored if `poll_types` set.
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects. Defaults to false.
`include_poll_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all poll objects. Defaults to false.
