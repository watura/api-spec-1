### Authentication Web Flows

#### Setup

Set up at least one redirect URI in the Developer area for your client.

Client-side flow is generally used for Javascript and other situations where the code could be inspected by a 3rd party, and they could see your `client_secret`.


#### Server-side flow

Start by making this <span class="method method-get">GET</span> call:

```
https://pnut.io/oauth/authenticate
?client_id=[client ID]
&redirect_uri=[redirect URI]
&scope=[space-delimited scopes]
&response_type=code
```

*To always prompt the user for authorization of scopes, even if they already have, use the `https://pnut.io/oauth/authorize` endpoint instead.*

This will direct the user to a page to authorize your client for the given scopes. If they approve that, it will redirect them to your redirect URI with `/?code=[CODE]` appended.

If the user decides *not* to authorize your client, they will be redirected to your <code>redirect URI</code> with `/?error_message=resource+owner+denied+your+app+access&error=access_denied` appended.

Now make a <span class="method method-post">POST</span> call with what you now have in the URL-encoded body (with a `Content-Type` of `application/x-www-form-urlencoded`):

```bash
curl "https://api.pnut.io/v0/oauth/access_token" \
-d "client_id=${CLIENT_ID}" \
-d "client_secret=${CLIENT_SECRET}" \
-d "code=${CODE}" \
-d "redirect_uri=${REDIRECT_URI}" \
-d "grant_type=authorization_code" \
-X POST
```

A JSON response will be returned in the form of:

```json
{"access_token":ACCESS_TOKEN, "token":{...}, "user_id":USER_ID, "username":USERNAME}
```




#### Client-side flow

Start with this <span class="method method-get">GET</span>:

```
https://pnut.io/oauth/authenticate
  ?client_id=[client ID]
  &redirect_uri=[redirect URI]
  &scope=[space-delimited scopes]
  &response_type=token
```
    
*To always prompt the user for authorization of scopes, even if they already have, use the `https://pnut.io/oauth/authorize` endpoint instead.*

This will direct the user to an authorization page just like the server-side flow. If they approve the scopes for your client, they will be redirected to your `redirect URI` with `/#access_token=[token]` appended.

If the user decides *not* to authorize your client, they will be redirected to your `redirect URI` with `/#error_message=resource+owner+denied+your+app+access&error=access_denied` appended.