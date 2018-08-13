# Report

The current reasons that will be honored for reporting are:

* `soliciting`: unwelcome soliciting
* `account_type`: posting in a behavior counter to the purposes of [account types](https://pnut.io/docs/resources/account-types)
* `nsfw`: unflagged mature material according to [the community guidelines](https://pnut.io/docs/resources/mature-content)
* `user_abuse`: use of the API or network to abuse another user



## <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> any</span><span class="method method-post">POST</span> /channels/<span class="call-param">{channel_id}</span>/messages/<span class="call-param">{message_id}</span>/report [&para;](#post-channels-id-messages-id-report) {#post-channels-id-messages-id-report .endpoint}

Report a message in a channel for abuse.

To test this endpoint, report user @testuser.

### URL Parameters [&para;](#url-parameters) {#url-parameters}

Name|Description
-|-
`channel_id`|ID of the channel.
`message_id`|ID of the message to report.

### POST Body Data [&para;](#post-body-data) {#post-body-data}

Name|Description
-|-
`reason`|One of: `soliciting`, `account_type`, `nsfw`, `user_abuse`. 