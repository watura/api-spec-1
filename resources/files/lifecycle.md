### File Lifecycle

For an explanation of how to attach files to other objects, read [How To File](../../how-to/file).



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> varies</span><span class="method method-post">POST</span> /files [<i class="fa fa-paragraph" aria-hidden="true"></i>](#post-files) {#post-files .endpoint}

Create a file placeholder or a complete file. `type`, `kind`, and `name` are necessary. By default, the file will be private.

If creating a file placeholder, it can be form data or a Content-Type of `application/json`.

If creating a complete file the Content-Type must be `multipart/form-data`, and the `content` key must be the file.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/files" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
  \"type\":\"com.example.site\",
  \"name\":\"That Thing!\",
  \"kind\":\"other\"
}" \
    -X POST
```

Returns the created file details

```json
{
  "meta": {
    "code": 201
  },
  "data": {
    "id": "72",
    "is_public": false,
    "created_at": "2017-07-25T15:14:42Z",
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
    "upload_parameters": {
      "method": "POST",
      "url": "https://api.pnut.io/v0/files/72/content"
    }
  }
}
```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> varies</span><span class="method method-put">PUT</span> /files/<span class="call-param">{file_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-files-id) {#put-files-id .endpoint}

Update a file. Only `name`, `is_public`, and `raw` can be updated. `PUT` and `PATCH` may be used.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/files/73" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
  \"name\":\"butternut squash\"
}" \
    -X PUT
```

Returns the updated file

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "73",
    "is_public": false,
    "created_at": "2017-07-25T15:19:02Z",
    "name": "butternut squash",
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



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> varies</span><span class="method method-put">PUT</span> /files/<span class="call-param">{file_id}</span>/content [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-files-id-content) {#put-files-id-content .endpoint}

Set a file placeholder's content.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/files/75/content" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -F "content=@somethingtoupload.jpg" \
    -X PUT
```

Returns 204 on success

```json

```




#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> varies</span><span class="method method-delete">DELETE</span> /files/<span class="call-param">{file_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-files-id) {#delete-files-id .endpoint}

Delete a file. This will not disassociate a file with any other objects (posts, messages...).

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/files/72" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE
```

Returns the deactivated file

```json
{
  "meta": {
    "code": 200
  },
  "data": {
    "id": "72",
    "is_public": false,
    "created_at": "2017-07-25T15:14:42Z",
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
    "is_deleted": true
  }
}
```