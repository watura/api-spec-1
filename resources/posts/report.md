### Report

The current reasons that will be honored for reporting are:

* `soliciting`: unwelcome soliciting
* `account_type`: posting in a behavior counter to the purposes of [account types](https://pnut.io/docs/resources/account-types)
* `nsfw`: unflagged mature material according to [the community guidelines](https://pnut.io/docs/resources/mature-content)
* `user_abuse`: use of the API or network to abuse another user



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> any</span><span class="method method-post">POST</span> /posts/<span class="call-param">{post_id}</span>/report [<i class="fas fa-paragraph"></i>](#post-posts-id-report) {#post-posts-id-report .endpoint}

Report a post for abuse.

To test this endpoint, report user @testuser.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`post_id`|ID of the post to report.

##### POST Body Data [<i class="fas fa-paragraph"></i>](#post-body-data) {#post-body-data}

Name|Description
-|-
`reason`|One of: `soliciting`, `account_type`, `nsfw`, `user_abuse`. 