### Scopes

`scope` is a space- or comma-separated list of which parts of the API your app can access on behalf of an authenticated user.

This is what a user is shown by pnut.io for each scope they are authorizing:

* **basic** see basic information about you
* **stream** read your post streams
* **write_post** create and interact with your posts
* **follow** add and remove follows, mutes, and blocks for you
* **update_profile** update your name and other profile information
* **presence** update your presence
* **messages** send and receive public and private messages
* **public_messages** send and receive public messages
* **files** manage your files
* **email** access your email address


### Usage

#### Extended Scopes

It's encouraged that you use extended scopes whenever reasonable, as it will reduce how much your app needs to filter out, and reduce the surface area for users' data to go places they don't want it to.

Channels and Files currently allow extended scopes. Extended scopes allow you to only authorize use of the channel types that your app needs access to. For example, if you only will be dealing with private messages, you should request the `messages:io.pnut.core.pm` scope. If your app has its own public-only channel type, you could request the `public_messages:com.example.site` scope. Or if it only needs to view and delete files for itself, you could request `files:com.example.site` access.


#### Changing Scopes

If the scopes you initially requested have changed, your users may have authorized some, but not all, of those scopes. If so, you can send them back through the authorization flow and it will ask for the new scopes to be allowed.

Your client can tell what scopes a user has authorized for your client by the `X-OAuth-Scopes` return header on a request, or by directly requesting their [Token](../resources/token#get-token).


### App Tokens

In the documentation, an <span class="endpoint-meta" style="float:none"><i class="fa fa-lock" aria-hidden="true"></i> app</span> scope indicates that an app token is required for the endpoint.


### Notes

#### basic

The `basic` scope only allows access to any endpoints in the API that require <span class="endpoint-meta" style="float:none"><i class="fa fa-lock" aria-hidden="true"></i> any</span> access token. If any other scope is authorized, `basic` is redundant.


#### files

This scope is not needed for uploading files. It allows clients to update, attach, and delete files without `file_token`s.

##### Special Extended File Scopes

There are two special file scopes: `files:core_audio` gives access to all files with `kind: audio`, and `files:core_image` gives access to all files with `kind: image`. These do not currently trigger App Stream objects; specific file types or the whole `files` scope would need to be specified to use App Streams with files.


#### email

When the `email` scope is authorized, the user's tokens will include their email.

`email` cannot be authorized for the first time through Password Flow.

App Streams do not notify of E-mail address changes.