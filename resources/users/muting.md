### User Muting

Muting a user will prevent them from being visible to the muting user unless specifically requested.



#### <span class="endpoint-meta"><i class="fas fa-lock"></i> any</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/muted [<i class="fas fa-paragraph"></i>](#get-users-id-muted) {#get-users-id-muted .endpoint}

Retrieve a list of muted users. Users may only see their own list of muted users.
    
##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-1) {#url-parameters-1}

Name|Description
-|-
`user_id`|ID of the user whose list of muted users to retrieve
    
##### Example {.example-code}
    
```bash
curl "https://api.pnut.io/v0/users/me/muted" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```
            
Returns a list of users
            
```json
"call for example 1"
```
    

#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> follow</span><span class="method method-put">PUT</span> /users/<span class="call-param">{user_id}</span>/mute [<i class="fas fa-paragraph"></i>](#put-users-id-mute) {#put-users-id-mute .endpoint}

Mute a user. Muted users will not appear in future requests.
    
##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`user_id`|ID of the user to mute
    
##### Example {.example-code}
        
```bash
curl "https://api.pnut.io/v0/users/@testuser/mute" \
    -X PUT \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```
            
Returns the muted user
            
```json
"call for example 2"
```
    
    
#### <span class="endpoint-meta"><i class="fas fa-lock"></i> | <i class="fas fa-user"></i> follow</span><span class="method method-delete">DELETE</span> /users/<span class="call-param">{user_id}</span>/mute [<i class="fas fa-paragraph"></i>](#delete-users-id-mute) {#delete-users-id-mute .endpoint}

Unmute a user.
    
##### URL Parameters [<i class="fas fa-paragraph"></i>](#url-parameters-3) {#url-parameters-3}

Name|Description
-|-
`user_id`|ID of the user to unmute
    
##### Example {.example-code}
        
```bash
curl "https://api.pnut.io/v0/users/@testuser/mute" \
    -X DELETE \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```
            
Returns the unmuted user
            
```json
"call for example 3"
```