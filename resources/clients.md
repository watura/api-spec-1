### Clients

Client name can contain any Unicode characters. *Be sure to escape it if necessary.*


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> any</span><span class="method method-get">GET</span> /users/<span class="call-param">{user_id}</span>/clients [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-id-clients) {#get-users-id-clients .endpoint}

Retrieve a list of active clients created by a user.

##### URL Parameters

Name|Description
-|-
`user_id`|ID of the user to list clients from

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/8/clients" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of clients

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "http://xyz.s3rv.com",
      "name": "Broadsword"
    },
    {
      "id": "4lARtAs5HQOzhsq9f6X6uhwKbsKjWHKS",
      "link": "https://chrome.google.com/webstore/detail/brusque/bohjpenpllkadgmknlgkahfbiepenhkj",
      "name": "Brusque"
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> any</span><span class="method method-get">GET</span> /clients/<span class="call-param">{client_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-clients-id) {#get-clients-id .endpoint}

Retrieve details on a public client, by client ID.

##### URL Parameters

Name|Description
-|-
`client_id`|ID of the client to retrieve

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/clients/3PFPMSet53RutGINA8e5HWqYg_UCDHad" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns the detailed client object

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "created_at": "2016-09-10T13:11:06Z",
    "created_by": {...},
    "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
    "link": "http://xyz.s3rv.com",
    "name": "Broadsword",
    "posts": 1940,
    "content": []
  }
}
```