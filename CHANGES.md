Follow Pnut API updates <a href="https://api.pnut.io/v1/feed/rss/users/@pnutapi/posts" rel="alternate" type="application/rss+xml">via RSS</a>

# <span class="orange">Changes</span>


## [v1.1.0](/docs/changes/1.1.0) {#1.1.0}

### Features

* "Welcoming committee" option for email digests
* User followers and following can be ordered by last_post_id, followed_at, id
* User search can filter by is_following, is_follower
* New "256" post explore stream

### Fixes

* Personal Data Request Broken on v1
* Not all Chat Room HTML Converted to Entities
* Changing account to bot does not properly register it as bot
* Changing account to feed left some follower data intact
* Developers could not create new clients
* V0 Poll raw was showing in new v1 format
* Channel Subscribers sometimes showing duplicates

*Released 2021-07-30*



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
* Posts and Messages in User and App Streams
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




## [Archived](/docs/changes/archived)