Follow Pnut API updates <a href="https://api.pnut.io/v0/feed/rss/users/@pnutapi/posts" rel="alternate" type="application/rss+xml">via RSS</a>

# <span class="orange">Changes</span>

* [0.9.1](#0.9.1)
* [0.9.0](#0.9.0)
* [0.8.0](#0.8.0)
* [0.7.7](#0.7.7)
* [0.7.6](#0.7.6)
* [0.7.5](#0.7.5)
* [0.7.4](#0.7.4)
* [0.7.3](#0.7.3)
* [0.7.2](#0.7.2)
* [0.7.1](#0.7.1)
* [0.7.0](#0.7.0)
* [0.6.0](#0.6.0)
* [0.5.1](#0.5.1)
* [0.5.0](#0.5.0)
* [0.4.5b](#0.4.5b)
* [0.4.5](#0.4.5)
* [0.4.4](#0.4.4)
* [0.4.3](#0.4.3)
* [0.4.2](#0.4.2)
* [0.4.1](#0.4.1)
* [0.4.0](#0.4.0)
* [0.3.0](#0.3.0)


## [2018-09-13](#0.9.1) v0.9.1 {#0.9.1}

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


## [2018-08-13](#0.9.0) v0.9.0 {#0.9.0}

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



## [2018-03-24](#0.8.0) v0.8.0 {#0.8.0}

### Features

* Polls
* New users are highlighted on the Invites page

### Changes

* Emails on account lock out and new recent IP login
* Password Flow authorization emails now express what new scopes are authorized
* Basic stats are public
* `avatar_image` included in channels when `?include_limited_users=1` query parameter is set
* Links with emoji in the domain are recognized as links
* @xyz's app *Beta* now uses the subdomain https://beta.pnut.io and is encouraged as users' first app

### Fixes

* Text file encoding was ignored on upload
* File names used the file token for its name when downloaded, instead of original file names
* Some instabilities with database handling/what happened if there was a bug
* Users could make their own posts trend



## [2018-01-14](#0.7.7) v0.7.7 {#0.7.7}

### Features

* API Documentation app can be authorized, allowing you to make API calls from documentation and see the response live. The examples are editable on-page

### Changes

* Link parsing improvements
* Adjusted notification email timing
* Post and message URI Templates must use `{object_id}` instead of `{post_id}` in links
* Documentation includes type of access token required for endpoints (app vs user)

### Fixes

* Failed login went to MFA login
* `content.html` now begins with `<span itemscope itemtype="https://pnut.io/schemas/Post">` instead of `<span itemscope itemtype="https://pnut.io/schemas/Post">` to follow [microdata spec](http://schema.org/docs/gs.html#microdata_itemscope_itemtype)



## [2017-12-10](#0.7.6) v0.7.6 {#0.7.6}

This is a bug fix update to pnut.io.

### Features

* Option to require OTP passwords for password flow authentications

### Changes

* One-Time Passwords now create a short random string for a name, instead of user input
* More clarity on profile update form
* MFA login now allows "Remember login" cookie but requires the TOTP code. A failed attempt or leaving the page will unset the "Remember login" cookie.
* Web Flows and Password Flow return much more specific feedback when something is not set properly

### Fixes

* Password form validation required a digit and uppercase, which is not supposed to be required anymore
* Failed MFA login would redirect to the normal login without client authorization details, if they had been set



## [2017-11-30](#0.7.5) v0.7.5 {#0.7.5}

### Features

* Pnut.io account area translations
* New Privacy page includes mutes, blocks, and new function to limit who can create new private message channels with you
* Bookmark E-mail notifications option for pnut badge supporters
* App Streams support `raw` by setting appropriate query parameters on the websocket link

### Changes

* Developer client "tokens" are no longer a thing; instead, new clients can be made by developers after a certain period
* `kind` is no longer required on file upload; you may juggle whether to specify `kind`, `mime_type`, neither, both
* `locale` limited to smaller list; more locales should be added on demand and as supportable
* `email` scope is not authorizable over Password Flow, to prevent possible privacy concern
* Link entity parsing adjusted (now includes links preceded by parenthesis)
* Message streams now allow negative `count` (`?count=-4`)
* App Streams now can differentiate between revised, reposted, and newly created or deleted posts

### Fixes

* Numerous possible edge cases with app streams returning partial objects



## [2017-11-16](#0.7.4) v0.7.4 {#0.7.4}

### Features

* App directory "early access" and "bot" categories
* Tokens can be assigned a "token group" on creation, and tokens can be revoked for an app based on IP address and token group
* `kind: audio` file type recognizes MP3, FLAC, and WAVE files
* `email` scope has been added, which adds `email` to user tokens
* `files:core_image` and `files:core_audio` special scopes have been added, giving access to their respective `kind` of files
* oEmbed endpoint for posts and files
* Endpoints for reporting posts and messages
* `newcomers` post explore stream, including users' first 50 posts
* Post, channel, and message searches allow `?raw_types` parameter
* `io.pnut.core.channel.avatar` and `io.pnut.core.channel.cover` raw types

### Changes

* RSS moved from https://pnut.io/feed/rss/ to https://api.pnut.io/v0/feed/rss/ (old links redirect)
* Canonical posts and user profiles direct to @xyz's [beta app](https://beta.pnut.io)
* Notifications are silenced within 30 seconds of previous notifications of the same type, and channel notifications are silenced if the user has a stream marker ahead of the message
* Developers can "remember" pnut.io login

### Fixes

* `raw` properly catches any improper values for `value`
* Some cases where objects wouldn't be sent to app streams
* User editing reverse markdown was broken with multiple markdown links
* New developers' existing apps were not automatically made usable by other users
* Bot and feed users' mentions did not correctly go to mention streams
* `?include_message_html=0` was ignored



## [2017-10-14](#0.7.3) v0.7.3 {#0.7.3}

This is a minor update to pnut.io.


### Changes

* Users can now sign up for an account with a pnut badge if they don't have an invite
* E-mail notifications happen instantaneously, then follow up with a digest of more of the same soon after
* Password flow will return error for invalid scopes
* Can remove verified domain from profile
* Invites page improved
* Languages and timezones limited to finite list instead of dynamically generated list
* Enabling MFA requires a TOTP code up front, before enabling


### Fixes

* Password flow didn't allow extended scopes
* `GET /users/me/channels` did not work with only extended scopes authorized
* No longer authorizes an extended scope if its basic scope has already been authorized





## [2017-09-30](#0.7.2) v0.7.2 {#0.7.2}

This is a minor feature update to pnut.io.

### Features

* App Directory reorganized into categories, multiple platforms
* Apps can now be "recommended" by users
* Post and message stream `meta` now includes `deleted_ids` and `revised_ids`, which are lists of post or message IDs that have been deleted or revised since `since_id`
* pnut badges added to profiles; supporting users may opt in to include `badge: {object}` on their user object


### Changes

* pnut.io front page redesign


### Fixes

* `guid` was still included on some posts and users
* Creating App Streams did not handle some errors clearly




## [2017-09-10](#0.7.1) v0.7.1 {#0.7.1}

This is a minor feature update to pnut.io.

### Features

* Personal data exports may be requested in the "Data" section of your account (*Currently does not include files)
* Numerous new characteristics for developers to note about their apps, including pictures
* API errors will often include referenceable `meta.error_id` on 500 responses


### Changes

* `/users/me/actions` now combines multiple objects in the `objects` list for the same action commited by different users
* Front page and app pages redesigned
* Link parsing should be operational; API will retrieve title and description for a link
* Removed *all* GUID properties (posts, users, messages)


### Fixes

* RSS tag feeds of multibyte character tags would not load




## [2017-08-27](#0.7.0) v0.7.0 {#0.7.0}

This is a major feature update to pnut.io.

### Features

* User, post, channel, and message search
* Derivative files
* Auto-generated thumbnails for images


### Changes

* File link expiration extended
* `?include_directed_posts=0` does not exclude your own posts
* Replies to your own posts do not add that thread to the Conversations explore stream
* App streams allow the access token to be included in the header or query parameter, like other API calls
* A message in a PM channel will re-subscribe any users who haven't muted the channel
* Improved domain verification on profiles using `rel="me"` link
* TOTP login authentication is available to everyone


### Fixes

* `/users/{user_id}/clients` not retrieving all active clients in some cases
* TOTP authentication setup
* PM not able to find existing channel in some cases
* Owners and full-ACL users not able to delete others' messages in non-PM channels
* Complex tags in posts not rendered as links on pnut.io
* `redirect_uri` did not work with an edge case




## [2017-07-25](#0.6.0) v0.6.0 {#0.6.0}

This is a major feature update to pnut.io.

### Features

* File API
* Pay-what-you-want tier!
 * Repost and follow E-mail notifications
 * RSS feed of personal and unified streams
 * File Storage
 * MFA logins (TOTP option)
* Added [microformats2](http://microformats.org/wiki/microformats2) to pnut.io posts and profiles
* Added `markdown_text` to user profile when retrieving own profile (helpful for editing)
* Including `&simple_login=1` on web authentication flows now shows an embed-friendly page for oauth


### Changes

* Consolidated some account management areas
* Increased invite limit from 5 to 7
* Clarified activation process on new sign up
* Notification E-mails are now digests
* Avatars and cover images limited to 2097152 and 4194304 bytes, instead of 2000000 and 4000000 bytes
* Posts from bots will not add threads to the "Conversations" explore stream
* pnut.io now reverses markdown when editing your profile


### Fixes

* Password recovery E-mail address was case-sensitive
* "Users" count on user objects (number of users invited) was incorrect
* Deleted messages were not being sent to App Streams
* Channel owner access was denied in an edge case

Note that after a year, current developers will have to pay $10/year for developer access.




## [2017-04-30](#0.5.1) v0.5.1 {#0.5.1}

This is a minor feature and bug fix update to pnut.io.

### Features

* The first developer to authorize an extended scope can now customize a description of what it is used for, when users authorize the scope in the future ("Content Types" in dev area)
* Users can change username once, and can change capitalization as often as they want, from pnut.io profile settings
* Including `#nsfw` in a post automatically marks it as "Not Safe for Work", unless explicitly marked otherwise
* Including `?exclude_channel_types=` on channel streams excludes the given types from the stream (opposite of `?channel_types=`)
* Including `?include_limited_users=1` on subscribed channel streams and individual channel calls will include users as limited objects in the ACL instead of user IDs only
* "Missed Conversations" explore stream added (random posts that had no interactions)

### Changes

* Activity log now includes administrative events (when an admin makes you a developer, suspends your account, etc.)
* Bare links are now parsed differently, and will accept more valid links, including IPv4/6 addresses

### Fixes

* Emoji tag streams did not function on pnut.io
* `/users/{user_id}/posts` now returns the user's posts even if an authorized user requests it after blocking or muting them




## [2017-04-15](#0.5.0) v0.5.0 {#0.5.0}

This is a feature update to pnut.io.

### Features

* App tokens
* App Streams
* Umlauts, emoji, foreign characters allowed in tags
* Logo
* Many new documents, some vague

### Changes

* Redirect URIs can now have query parameters and still validate
* Link entities will not include redundant phishing protection
* API documentation is rearranged, and included verbatim from the GitHub repository
* OAuth now warns when the client is requesting a non-HTTPS <code>redirect_uri</code>, and better displays what is being authorized
* pnut.io now shows oembed images on posts. Other minor improvements
* The "Support Us" page now includes message counts in the stats
* Mentions in a post are now more likely to be considered "leading mentions"
* Messages do not include <code>counts.replies</code> at all (for now)

### Fixes

* Multiple manually submitted links would fail to be parsed
* Invites were not calculated correctly (so were seldom given out)
* Redirecting after login and related edge cases are improved around OAuth




## [2017-03-14](#0.4.5b) v0.4.5b {#0.4.5b}

This is a minor feature update to pnut.io.

### Features

* "Support Us" page has basic stats
* New "Activity" account page, which shows the last 10 significant actions made in your account (logins, password changes, etc.)




## [2017-03-03](#0.4.5) v0.4.5 {#0.4.5}

This is a minor feature update to pnut.io.

### Features

* Invites are now created automatically
* Each app in the directory now has its own simple page, with expanded description
* Can hide posts directed at people you do not follow
* Can hide "copy mentions" on the mentions endpoint
* New Explore streams for posts that are Conversations, Trending, and Photos
* New endpoint `/users/me/channels/existing_pm` retrieves a channel between a given set of users, if it exists
* The subscribed channels endpoint (`/users/me/channels/subscribed`) includes count for unread PMs in the meta field
* Can now add "notes" to unused invites, to easily track what you're doing with them


### Changes

* PM notifications are strictly indicators that you have unread PMs, and no longer contain the text of the messages
* Better HTML version of the mention notification E-mail
* Underscores now allowed in tags
* Small improvement to threads and user profiles on pnut.io
* Clients now require approval before being published to the app directory


### Fixes

* Deauthorizing a client that doesn't have any tokens now deauthorizes its scopes properly
* Deleted posts should no longer show up in older threads/streams (as well as other bleeding possibilities)
* Channels were showing up multiple times (a subscription bug) on the subscribed channels endpoint
* `count=-**n**` now works as expected on post streams
* Text with E-mail addresses in it should not be parsed as links or mentions




## [2017-02-04](#0.4.4) v0.4.4 {#0.4.4}

This is a minor update to pnut.io.

### Features

* All non-developers now have the ability to create one client that only they can authorize
* Users who reposted or bookmarked posts can be included by including query parameters `include_reposted_by` and `include_bookmarked_by`
* Basic view of tags at `https://pnut.io/tags/tag` and RSS for them at `https://pnut.io/feed/rss/posts/tags/tag`


### Changes

* Non-markdown non-client-supplied links are restricted to known TLDs
* Mentions are allowed at the end of word breaks (think: `"@`, `'@`, `(@`)
* Improved pnut.io user profiles and threads


### Fixes

* Suspended and deleted accounts no longer retrievable from pnut.io
* `public_messages` and `messages` being authorized could result in only `public_messages` access
* User RSS handles reposts properly




## [2017-01-25](#0.4.3) v0.4.3 {#0.4.3}

This is a minor update to pnut.io.

### Features

* `include_marker=1` option available on all stream marker-capable endpoints

### Changes

* "-" was not handled correctly in link entities
* Mutes were making messages and post actions appear multiple times




## [2017-01-23](#0.4.2) v0.4.2 {#0.4.2}

This is a minor update to pnut.io.

### Features

Submitting `entities.links` on posts, messages, and users works (it is incongruously entities.links on posts and messages, but content.entities.links on users)
Markers are always included on `GET /channels/{channel_id}/messages` and can be included on `GET /channels/{channel_id}` with `include_marker=1` in the query


### Changes

Deactivating accounts is more straight-forward and consistent


### Fixes

Unicode `pos` and `len` on entities was not handled properly
Tags inside markdown were parsed, breaking html/text
`GET /users?ids=` can now be @-usernames and user IDs
`is_nsfw` was not consistently handled (and sometimes ignored)




## [2017-01-15](#0.4.1) v0.4.1 {#0.4.1}

This is a minor update to pnut.io.

### Fixes

* Usernames were case-sensitive in password_flow
* `io.pnut.core.chat`-type channels were not creatable
* Public channels included `you` in the ACL unnecessarily when not authenticated
* Deleting channel messages sometimes did not work
* `/users/me/actions` not returning follow actions under some circumstances




## [2017-01-07](#0.4.0) v0.4.0 {#0.4.0}

This is a major update to pnut.io. The following is notable.

### Features

* `raw` data on posts, messages, users, and channels
* Stream markers can be updated to the latest ID on post or message creation
* Channel-specific sticky messages
* Channel thread endpoint


### Changes

* Revising posts saves the complete original post, where it used to only preserve the original `text` and `html`
* `X-API-Version` header changed to a major.minor.bugfix format, though in 0.x.x, all are minor or bugfix changes


### Fixes

* Avatars/covers not showing on pnut.io profiles
* `/users/me/channels/subscribed` was ordered by ID only, now by most recent message or most recent creation, with clarifying `pagination_id`
* Requesting a token did not return the list of scopes for it
* New user creation did not properly handle the created "follow" action
* Calls for user avatars/covers were not forwarding query parameters




## [2016-11-24](#0.3.0) v0.3.0 {#0.3.0}

This is a major update to pnut.io. The following is notable.

### Features

* More capable app directory
* Mutes and blocks management from pnut.io
* Channels
* Stream markers
* Client secret reset option


### Changes

* `pagination_id` added to user, post, message, and channel objects in paginated responses
* Following, followers, muted, and blocked user lists are now paginated
* PUT/DELETE bookmark returns the post bookmarked
* `presence` endpoints now include a timestamp of the last time a user was seen (even when their status is not "offline")
* Bookmarks are no longer restricted to the bookmarker
* `invited_by` no longer included on user objects (simply able to look it up on the invite tree on pnut.io)
* Developers required to enter password on every login
* Markdown links and normal links are parsed by default. To prevent parsing, must include `entities.parse_links=0`
* Requests for tokens respond with errors closer to OAuth 2.0 guidelines
* Removed `/posts/streams/feed`, `/posts/streams/link`, `/posts/streams/domain`, `/posts/streams/link` (more appropriate to retrieve via future search)
* Moved `/system/configuration` and `/system/statistics` to `/sys/config` and `/sys/stats`


### Fixes

* Inviting a user now creates a "follow" action when they auto-follow the inviter
* Blocks are missing fewer edge cases
* Revising a post parsing markdown links and normal links improperly
* Users' list of actions executed against them could only filter by one type; now any number