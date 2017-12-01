### File Lifecycle

For an explanation of how to attach files to other objects, read [How To File](../../how-to/file).



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> files</span><span class="method method-post">POST</span> /files [<i class="fa fa-paragraph" aria-hidden="true"></i>](#post-files) {#post-files .endpoint}

Create a file placeholder or a complete file. `type`, `kind`, and `name` are necessary. By default, the file will be private.

If creating a file placeholder, it can be form data or a Content-Type of `application/json`.

If creating a complete file the Content-Type must be `multipart/form-data`, and the `content` key must be the file.

##### POST Body Data [<i class="fa fa-paragraph" aria-hidden="true"></i>](#post-body-data-1) {#post-body-data-1}

Name|Description
-|-
`content`|__Required__ (if uploading in a single step) Key of the uploaded file
`kind`|__Required__ One of: `other`, `image` (for JPEG, GIF, PNG), `audio` (for WAVE, MP3, FLAC. up to 52428800 bytes)
`name`|__Required__ 256-character name or description (to be displayed and attached to the object; a random key will actually be assigned for the filename)
`type`|__Required__ Reverse domain name-style identifier of the file type. E.g., `com.example.site`. Searchable
`is_public`|If true, file is public
`sha256`|API will check the file's SHA256 checksum against this, and return an error if they do not match
`mime_type`|If the API cannot determine mime_type, it will use this
`{name}` + `_image_thumb_200s`|Key for custom derived thumbnail, 200 by 200 pixels, resized and cropped. If not included, API will try to create one, for images.
`{name}` + `_image_thumb_960r`|Key for custom derived thumbnail, within 640 width and 960 height. If an uploaded image has smaller proportions, one will not be created automatically.


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



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> files</span><span class="method method-patch">PATCH</span> /files/<span class="call-param">{file_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-files-id) {#put-files-id .endpoint}

Update a file's details. Only `name`, `is_public`, and `raw` can be updated.

If a file is ever made public, it could be accessed by others indefinitely using an embedded `file_token_read`, or for a while after via the cache. To make a public file secure again, delete it and upload it again as a new file.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters) {#url-parameters}

Name|Description
-|-
`file_id`|ID of the file to update

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



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> files</span><span class="method method-put">PUT</span> /files/<span class="call-param">{file_id}</span>/content/<span class="call-param">{derived_key}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-files-id-content-key) {#put-files-id-content-key .endpoint}

Upload a new derivative file. You may only do this with an existing file placeholder (an incomplete file).

This is particularly useful if you want to include alternative versions of a file, such as different sizes of images, custom thumbnails instead of auto-generated thumbnails, or different music or video formats of a file.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-2) {#url-parameters-2}

Name|Description
-|-
`file_id`|ID of the file placeholder to create a derivative file for
`derived_key`|Multipart key to the file. Keys starting with `core_` are reserved. `core_image_200s` and `core_image_960r` can be set, but have to be 200x200 pixels and within 640x960 respectively, and the same mime type as `file_id`.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/files/69/content/core_image_200s" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
```

Returns 204 on success

```json

```



#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> files</span><span class="method method-put">PUT</span> /files/<span class="call-param">{file_id}</span>/content [<i class="fa fa-paragraph" aria-hidden="true"></i>](#put-files-id-content) {#put-files-id-content .endpoint}

Set a file placeholder's content. You may only do this with an incomplete file.

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-3) {#url-parameters-3}

Name|Description
-|-
`file_id`|ID of the file to set contents for

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




#### <span class="endpoint-meta"><i class="fa fa-lock" aria-hidden="true"></i> files</span><span class="method method-delete">DELETE</span> /files/<span class="call-param">{file_id}</span> [<i class="fa fa-paragraph" aria-hidden="true"></i>](#delete-files-id) {#delete-files-id .endpoint}

Delete a file. This will not disassociate a file with any other objects (posts, messages...).

##### URL Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#url-parameters-4) {#url-parameters-4}

Name|Description
-|-
`file_id`|ID of the file to delete

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