### File Lookup

To only retrieve files by certain types, include them in a comma-separated list in the query parameter like so: `file_types=com.butternutsquash.image,com.example.site`.



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> files</span><span class="method method-get">GET</span> /files/<span class="call-param">{file_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-files-id) {#get-files-id .endpoint}

Retrieve a file object.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`file_id`|ID of the requested file

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/files/69" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns the requested file details

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "69",
    "is_public": false,
    "created_at": "2017-07-25T14:50:46Z",
    "name": "recipes.odt",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "link": "https://broadsword.io",
      "name": "Broadsword"
    },
    "type": "com.example.site",
    "is_complete": false,
    "kind": "other",
    "user": {...}
  }
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> files</span><span class="method method-get">GET</span> /files [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-files) {#get-files .endpoint}

Retrieve a list of specified file objects. Only returns the first 200 found.

##### Query String Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#query-string-parameters) {#query-string-parameters}

Name|Description
-|-
`ids`|Comma-separated list of file IDs

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/files?ids=69,71" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of files

```json
{
  "meta": {
    "code": 200
  },
  "data": [
    {
      "id": "69",
      "is_public": false,
      "created_at": "2017-07-25T14:50:46Z",
      "name": "recipes.odt",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "https://broadsword.io",
        "name": "Broadsword"
      },
      "type": "com.example.site",
      "is_complete": false,
      "kind": "other",
      "user": {...}
    },
    {
      "id": "71",
      "is_public": false,
      "created_at": "2017-07-25T15:12:01Z",
      "name": "Another Thing!",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "https://broadsword.io",
        "name": "Broadsword"
      },
      "type": "com.example.site",
      "is_complete": false,
      "kind": "other",
      "user": {...}
    }
  ]
}
```


#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> files</span><span class="method method-get">GET</span> /users/me/files [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-users-me-files) {#get-users-me-files .endpoint}

Retrieve a list of files created by the authenticated user.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/files" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns a list of files

```json
{
  "meta": {
    "more": false,
    "min_id": "69",
    "max_id": "74",
    "code": 200
  },
  "data": [
    {
      "id": "74",
      "is_public": false,
      "created_at": "2017-07-25T15:20:23Z",
      "name": "That%20Thing!",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "https://broadsword.io",
        "name": "Broadsword"
      },
      "type": "com.example.site",
      "is_complete": false,
      "kind": "other",
      "user": {...},
      "pagination_id": "74"
    },
    {
      "id": "71",
      "is_public": false,
      "created_at": "2017-07-25T15:12:01Z",
      "name": "That Thing!",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "https://broadsword.io",
        "name": "Broadsword"
      },
      "type": "com.example.site",
      "is_complete": false,
      "kind": "other",
      "user": {...},
      "pagination_id": "71"
    },
    {
      "id": "70",
      "is_public": false,
      "created_at": "2017-07-25T15:06:43Z",
      "name": "That Thing!",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "https://broadsword.io",
        "name": "Broadsword"
      },
      "type": "com.example.site",
      "is_complete": false,
      "kind": "other",
      "user": {...},
      "pagination_id": "70"
    },
    {
      "id": "69",
      "is_public": false,
      "created_at": "2017-07-25T14:50:46Z",
      "name": "recipes.odt",
      "source": {
        "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
        "link": "https://broadsword.io",
        "name": "Broadsword"
      },
      "type": "com.example.site",
      "is_complete": false,
      "kind": "other",
      "user": {...},
      "pagination_id": "69"
    }
  ]
}
```