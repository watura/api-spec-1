Follow Pnut API updates <a href="https://api.pnut.io/v0/feed/rss/users/@pnutapi/posts" rel="alternate" type="application/rss+xml">via RSS</a>

# <span class="orange">Changes</span>


## [v1.0.0](/docs/changes/1.0.0) {#1.0.0}

*Note: v0.9.6 will continue to be supported as-is until further notice.*

### Features

* E-mail Digest Notifications
* New Channel Fields
* Chat Room Name on Messages in Streams
* Chat Room Rich Text Description
* Channel Explore Streams
* Changing Channel Owners
* Message Replies Count
* NSFW Reposts
* Search Improvements
* Polls Added to App Streams
* RSS Feeds Include Media

### Changes

Breaking

* User Streams and App Streams disabled for API v0 <span class="endpoint-meta">v0.9.6</span>
* file, token, and follow User Stream Events Include Data
* Private Message ACL Changes
* Poll Response Handling Changed
* Raw Objects Reformatted
* User Objects No Longer Overloaded
* User "users" Count Removed
* Channel Owner Renamed
* Message is_sticky Always Present
* References to "link" Now "url"
* Post Revision Now an Integer
* System Stats Endpoint Adjustment
* System Config Endpoint Adjustment
* Text Render Endpoint Adjustment
* Search Changes
* User Poll Response Stream

Minor

* "basic" Authentication Scope Always Included <span class="endpoint-meta">v0.9.6+</span>
* Error Responses
* Animated GIF Avatars
* Accepted Actions Against Reposts
* E-mail Notifications for Follow, Repost, Bookmark

Informational

* New TLDs Recognized <span class="endpoint-meta">v0.9.6+</span>
* Documentation Structure Reorganized


### Fixes

* Channel ACL Duplicates <span class="endpoint-meta">v0.9.6+</span>
* public_messages Scope Creep <span class="endpoint-meta">v0.9.6+</span>
* Updating User Badge <span class="endpoint-meta">v0.9.6+</span>
* Revised Post created_at Format <span class="endpoint-meta">v0.9.6+</span>
* Search Fixes <span class="endpoint-meta">v0.9.6+</span>
* International Punycode Links <span class="endpoint-meta">v0.9.6+</span>
* Error Handling of Multiple Messages or Posts by ID

*Released 2021-02-27*


## [v0.9.6](/docs/changes/0.9.6) {#0.9.6}

### Features

* Used invites view
* Simple QR code invite
* Chat room E-mail notifications
* RSS feed URI templates
* MFA backup code
* E-mail notification link presets

### Changes

* "API changes" documentation
* Markdown link length calculation documentation
* Marking all of a channel type as "read"
* Unread chat room count on subscribed channels
* Message search "replies" flag
* More flexible user messages scopes

### Fixes

* Localizations
* Poll search order

*Released 2020-05-02*


## [v0.9.5](/docs/changes/0.9.5) {#0.9.5}

### Features

* New `video` file standardization, on file uploads and oembeds
* Revert user images to defaults (`DELETE /users/me/cover` and `DELETE /users/me/avatar`)
* Invites now include a link to a QR code image of the invite, in addition to the copyable link and E-mail options
* When authorizing an app, users can directly uncheck requested permissions they do not want to allow
* The website defaults to light-mode, and uses CSS preferences for showing dark-mode
* Channel Search endpoint as RSS feed

### Changes

* `io.pnut.core.crosspost`-type raw items expanded with options for external user representation
* `embeddable_url` in oEmbeds now can use template URIs (`{object_id}`)
* `max_options` on polls can now be the total number of options, instead of one less than the total
* File `name` can be inferred from the uploaded file's name, if not included in the POST
* When a user no longer has any access tokens for an app, the app's scopes will be revoked, and the user will have to re-authorize scopes the next time a token is created
* Sending a message to User or App streams (websockets) will return a "pong" response
* User and App streams require a "ping" every 60 seconds, instead of every 50 seconds

### Fixes

* Personal data export files in zip file are now encoded properly for UTF-8
* `https://photos.pnut.io/{post_id}/{image_placement_order}` and `https://photos.pnut.io/{file_id}` oembed links now temporarily redirect to post threads on Beta
* Poll notifications could fire multiple times for a single participant
* Saving Invite notes redirected to a 404
* Upgrading to developer account failed
* Some complex channel searches would fail

*Released 2020-01-01*


## [v0.9.4](/docs/changes/0.9.4) {#0.9.4}

### Features

* `GET /sys/stats` includes `data.counts.users.today`, which is unique account IDs accessed in the current UTC day
* Entities now include `gopher://` links in addition to `http://`, `https://`, and `ftp://`
* Polls can optionally allow users to select multiple options, up to `max_options`
* Channel search can be ordered by `popularity`--how many messages have been made in the channel
* Channel search includes a basic text query of chat room names and descriptions
* `io.pnut.core.fallback_url` added to `raw` elements

### Changes

* Reposts include their reposted posts' `raw`
* `GET /users/{id}/presence` and `GET /presence` return limited users including avatar image, username, name
* `GET /token` now includes `markdown_text`
* Account badge and payment pages have been reorganized

### Fixes

* E-mail notifications for polls closing occurred regardless of notification setting
* Notification custom links not recognized
* Unmuting from Pnut.io
* First-time authorization after TOTP login failing to return Oauth state
* Post search and user file retrieval edge cases
* Documentation includes examples for user streams
* `markdown_text` on `GET /users/me` parsed some links improperly

*Released 2019-08-03*


## [v0.9.3](/docs/changes/0.9.3) {#0.9.3}

### Features

* E-mail "poll finished" notifications
* JPEG images with EXIF data will be rotated, and EXIF data will be stripped
* `GET /clients/{id}` includes the client's logo, if it has one
* `io.pnut.core.chat`-type message RSS feeds include the channel's name in the title and description

### Changes

* Poll responses can be changed until a poll closes
* Any member of a private message can sticky messages for the group
* E-mail notifications always include "canonical" links, even if custom links are set in notification settings
* `suppress_notifications` on App Streams now includes muted users

### Fixes

* Error updating user badges

*Released 2019-04-07*


## [v0.9.2](/docs/changes/0.9.2) {#0.9.2}

### Features

* Allow `/text/process` to render messages instead of posts, with a query parameter
* File `kind` can be inferred from file extension
* `io.pnut.core.channel-invite` raw now attaches the related channel's `name`, if a "chat" channel
* Markdown links with titles will show `title` on the object, not just embedded in `html`
* Users can specify link template used in notification E-mails

### Changes

* Improved documentation for searches, and templatized API example responses
* Known file extensions will be normalized lowercase
* Ellipsis (`…`) is ignored at the end of inline links
* Improved duplicate post handling
* Links handle parentheses more naturally
* Repost and bookmark E-mail notifications include the post's text
* Developer accounts are now a one-time fee of $42, instead of an annual subscription
* Tags can still include underscores in text and html, but lookups ignore them

### Fixes

* Account data page wouldn't show usage for non-Badge-holders
* Newly invited users did not register following the inviter
* oEmbed `raw` was accepting strings and non-Integer numbers for image width and height
* Gifted Pnut badges weren't accepted for one case
* Authorizing new client email included an empty client name
* `redirect_uri`s with special schemes (not "https") weren't recognized
* Post and message length was calculated with an approximation, now it uses the same calculation as in actual rendering
* Post search failed for some lookup combinations

*Released 2018-12-31*


## [v0.9.1](/docs/changes/0.9.1) {#0.9.1}

### Features

* Badge directory, earning, assigning, and setting by clients
* Added `mime_types` filter to files
* Added `+io.pnut.core.user` raw replacement value
* Post search and channel message endpoints are accessible from RSS
* New `poll_response` interaction when someone responds to your poll
* New `/users/me/polls/responses` endpoint

### Changes

* Improved documentation
* Alternative `/users/me/interactions` and `/posts/{post_id}/interactions` endpoints
* Tweaked post search
* Small performance improvements to all POST calls

### Fixes

* Audio file attached via oEmbed had faulty `url_expires_at`
* Server-side flow didn't preserve `state` parameter
* Could not delete polls
* Deleted messages didn't send over user and app streams

*Released 2018-09-13*


## [v0.9.0](/docs/changes/0.9.0) {#0.9.0}

### Features

* User Streams (user-specific websockets, like App Streams for individual users)
* Invited users now have 512MiB of free storage, ensuring everyone has some free storage
* Users may gift Pnut Badges to other users
* Basic poll search
* Get multiple polls by ID in a single call
* Bookmarks may be saved with `note`, which is only visible to the user who bookmarked it, when retrieving their own bookmarks
* Clients can limit what scopes can be authorized
* `/sys/stats` now includes `counts.clients.public`, tracking clients that are "active/public" and usable by more than just a single user
* Alternative API domain https://pnut-api-1.org
* App Streams messages and posts now include `meta.suppress_notifications`, and `meta.subscribed_user_ids` to simplify notifications
* `include_replies` and `include_mention_posts` query parameters for post streams
* `has_mentions` post search filter

### Changes

* Requesting account deletion requires password verification
* Only human account-types can respond to polls
* `is_your_response` on poll options changed to `true` or `false` from `1` or `0`
* App Streams now have connection- and subscription-level query parameters
* App Streams objects are more consistent
* User tokens return with `storage.total` in addition to `storage.available`.

### Fixes

* Some old avatars were not deleted
* `/users/{id}/cover` was not redirecting properly
* "Account locked out" was logged after single failed login attempt
* `include_user=0` returned empty string instead of user's ID for embedded users on file objects
* Following a user in rapid succession could cause multiple listings of a user in your follows or followings

*Released 2018-08-13*



## [Archived](/docs/changes/archived)