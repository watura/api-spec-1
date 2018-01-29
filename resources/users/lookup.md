### User Lookup


#### <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span> [<i class="fas fa-paragraph"></i>](#get-users-id) {#get-users-id .endpoint}

Retrieve a user object.

##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`user_id`|User ID or username with "@" symbol of the user to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the user object

```json
"call for example 1"
```


#### <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /users [<i class="fas fa-paragraph"></i>](#get-users) {#get-users .endpoint}

Retrieve a list of specified user objects. Only retrieves the first 200 found.

##### Query String Parameters [<i class="fas fa-paragraph"></i>](#query-string-parameters) {#query-string-parameters}

Name|Description
-|-
`ids`|Comma-separated list of user IDs. IDs are required; no other identifiers are allowed.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users?ids=4,12,1000" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of users

```json
"call for example 2"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-server"></i> app</span><span class="method method-get">GET</span> /apps/me/users/ids [<i class="fas fa-paragraph"></i>](#get-apps-me-users-ids) {#get-apps-me-users-ids .endpoint}

Retrieve a list of all user IDs that authorize the requesting app. It is not paginated.

Requires an app token.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/apps/me/users/ids" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of user IDs

```json
"call for example 3"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-server"></i> app</span><span class="method method-get">GET</span> /apps/me/users/tokens [<i class="fas fa-paragraph"></i>](#get-apps-me-users-tokens) {#get-apps-me-users-tokens .endpoint}

Retrieve a list of all user token objects that authorize the requesting app. Not currently paginated.

Requires an app token.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/apps/me/users/tokens" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of user tokens

```json
"call for example 4"
```