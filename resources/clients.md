### Clients

Client name can contain any Unicode characters. *Be sure to escape it if necessary.*


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> any</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/clients [<i class="fas fa-paragraph"></i>](#get-users-id-clients) {#get-users-id-clients .endpoint}

Retrieve a list of active clients created by a user.

##### URL Parameters

Name|Description
-|-
`user_id`|ID of the user to list clients from

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/8/clients" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of clients

```json
"call for example 1"
```


#### <span class="endpoint-meta"><i class="fas fa-lock"></i> any</span><span class="method method-get">GET</span> /clients/<span class="call-param">{client_id}</span> [<i class="fas fa-paragraph"></i>](#get-clients-id) {#get-clients-id .endpoint}

Retrieve details on a public client, by client ID.

##### URL Parameters

Name|Description
-|-
`client_id`|ID of the client to retrieve

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/clients/3PFPMSet53RutGINA8e5HWqYg_UCDHad" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the detailed client object

```json
"call for example 2"
```