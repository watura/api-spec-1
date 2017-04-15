### Scope
    
`scope` is a space- or comma-separated list of which parts of the API your app can access on behalf of an authenticated user.

#### Options

* **basic** see basic information about this user
* **stream** read this user's stream
* **write_post** create a new post as this user
* **follow** add or remove follows, mutes, and blocks for this user
* **update_profile** update a user's name and other profile information
* **presence** update user's presence
* **messages** all messages and channels
* **public_messages** only public channels and messages


#### basic

The `basic` scope only allows access to any endpoints in the API that require <span class="endpoint-meta" style="float:none"><i class="fa fa-lock" aria-hidden="true"></i> any</span> access token. If any scope *other than* `basic` is authorized, `basic` is redundant.

Channel requests usually vary by the ACLs of what is being requested. You may also authorize extended scopes for them, so you only retrieve the types of channels you need.


#### App Tokens

In the documentation, an <span class="endpoint-meta" style="float:none"><i class="fa fa-lock" aria-hidden="true"></i> app</span> scope indicates that an app token is required for the endpoint.


#### Extended Scopes

Channels are the only area of the API that currently allow extended scopes. Extended scopes allow you to only authorize use of the channel types that your app needs access to. For example, if you only will be dealing with private messages, you could request the `messages:io.pnut.core.pm` scope. If your app has its own public-only channel type, you could request the `public_messages:com.example.site` scope.


#### Changing Scopes

If the scopes you initially requested have changed, your users may have authorized some, but not all, of those scopes. If so, you can send them back through the authorization flow and it will ask for the new scopes to be allowed.

You can tell what scopes a user has authorized for your client by the `X-OAuth-Scopes` return header on a request, or by directly requesting their [Token](../resources/token#get-token).