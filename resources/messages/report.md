# Report

The current reasons that will be honored for reporting are:

* `account_type`: posting in a behavior counter to the purposes of [account types](https://pnut.io/about/resources/account-types)
* `nsfw`: unflagged mature material according to [the community guidelines](https://pnut.io/about/resources/mature-content)
* `soliciting`: unwelcome soliciting
* `user_abuse`: use of the API or network to abuse another user

Endpoints:

* [Report a message](#post-channels-id-messages-id-report)


## <span class="method method-post">POST</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span>/report {#post-channels-id-messages-id-report .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Report a message in a channel for abuse.

To test this endpoint, report a message by user [@testuser](/docs/resources/testuser).

### URL Parameters

Name|Description
-|-
`channel_id`|ID of the channel.
`message_id`|ID of the message to report.

### POST Body Data

Name|Description
-|-
`reason`|One of: `account_type`, `nsfw`, `soliciting`, `user_abuse`.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/channels/18/messages/0/report" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a 201

```json

```