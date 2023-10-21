# Scopes

`scope` is a comma-separated list of which parts of the API your app can access on behalf of an authenticated user.

This is what a user is shown by Pnut for each scope they are authorizing:

* [**basic**](#basic) - see basic information about you
* [**email**](#email) - access your email address
* [**files**](#files) - manage your files
* **follow** - add and remove follows, mutes, and blocks for you
* [**messages**](#messages) - send and receive public and private messages
  * **public_messages** - send and receive public messages
* [**polls**](#polls) - manage your polls
* **presence** - update your global presence
* **stream** - read your post streams
* **update_profile** - update your name and other profile information
* [**write_post**](#write_post) - create and interact with your posts





## Usage

### Extended Scopes

It's encouraged that you use extended scopes whenever reasonable, as it will reduce how much your app needs to filter out, and reduce the surface area for users' data to go places they don't want it to.

Channels, Files, and Polls currently allow extended scopes. Extended scopes allow you to only authorize use of the channel types that your app needs access to. For example, if you only will be dealing with private messages, you should request the `messages:io.pnut.core.pm` scope. If your app has its own public-only channel type, you could request the `public_messages:com.example.site` scope. Or if it only needs to view and delete files for itself, you could request `files:com.example.site` access.


### Choosing Scopes

When authorizing scopes, users will have the choice of not authorizing all new scopes. This is an example of what they might see:

<img src="/static/images/docs/Screenshot_Authenticate_App.png" style="border:1px solid #333" alt="Choosing scopes"/>


### Changing Scopes

If the scopes you initially requested have changed, or your users may have otherwise authorized some but not all of those scopes, you can send them back through the authorization flow and it will ask for the new scopes to be allowed.

Your client can tell what scopes a user has authorized for your client by the `X-OAuth-Scopes` return header on a request, or by directly requesting their [Token](../resources/token#get-token).

If your app needs to *remove* scopes for a user, you will have to delete all of the user's tokens individually. You can [request all tokens authorized for your app](../resources/users/lookup#get-apps-me-users-tokens), and [delete](../resources/token#delete-token) all of them for a user. Once all tokens are removed, the user will have to completely re-authenticate the app, and you can request different scopes.


## App Tokens

In the documentation, an <span class="endpoint-meta" style="float:none">app</span> scope indicates that an app token is required for the endpoint.


## Notes

### basic {#basic}

If any other scope is authorized, `basic` is redundant.

Because it is redundant, it will be included in the authorization options if any other scope is authorized. If your app is double-checking what scopes were authorized, be sure it does not get thrown off if it sees `basic`.

Any scope will allow access to any endpoints in the API that specify <span class="endpoint-meta" style="float:none">any</span> access token. That includes a user's...

* following
* followers
* muted
* blocked
* presence
* badges
* interactions
* bookmarks
* public clients
* ongoing operations

as well as abilities to...

* report a post or message
* set a stream marker
* delete user streams
* get your current token


### email {#email}

When the `email` scope is authorized, the user's tokens will include their email address.

`email` cannot be authorized by a user for the first time through Password Flow.

App Streams do not notify of email address changes.


### files {#files}

#### Uploading Files vs Managing Files

Clients that only upload files to attach to posts or messages don't need `files` authorized. If you already have `write_post` or a `messages` scope authorized, you can upload files.

If a client has a `files`-related scope, it will be able to retrieve, update, attach, and delete those files without including a `file_token`.

#### Special Extended File Scopes

There are two special file scopes: `files:core_audio` gives access to all files with `kind: audio`, and `files:core_image` gives access to all files with `kind: image`. These do not currently trigger App Stream objects; specific file types or the whole `files` scope would need to be specified to use App Streams with files.


### messages {#messages}

#### Updating presence in a channel

The `presence` scope is for global user's presence. If a user access token has access to a channel, it can update the user's presence in that channel. The `presence` scope isn't relevant to channel presence permissions.


### polls {#polls}

#### Uploading Polls vs Managing Polls

This scope works similarly to `files`, and is not needed to create and attach polls to posts and messages, but lets users attach and delete polls without a `poll_token`.


### write_post {#write_post}

`write_post` allows an app to create files and polls as well, so those can be created and attached using their returned "tokens".
