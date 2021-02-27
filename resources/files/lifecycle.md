# File Lifecycle

For an explanation of how to attach files to other objects, read [How To File](../../how-to/file).

Endpoints:

* [Create a file or placeholder](#post-files)
* [Update file metadata](#put-files-id)
* [Upload derivatives of a file](#put-files-id-content-key)
* [Complete a placeholder file](#put-files-id-content)
* [Delete a file](#delete-files-id)


## <span class="method method-post">POST</span> /files {#post-files .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">files</span>

Create a file placeholder or a complete file. By default, the file will be private.

If creating a file placeholder, it can be form data or a Content-Type of `application/json`.

If creating a complete file the Content-Type must be `multipart/form-data`, and the `content` key must be the file.

### POST Body Data

Name|Description
-|-
`content`|__Required__ (if uploading in a single step) Key of the uploaded file
`type`|__Required__ Reverse domain name-style identifier of the file type. E.g., `com.example.site`. Searchable
`name`|256-character name or description (to be displayed and attached to the object; a random key will actually be assigned for the filename). If not included, name of file uploaded will be used
`kind`|One of: `other`, `image` (for JPEG, GIF, PNG), `audio` (for WAVE, MP3, FLAC. up to 52428800 bytes), `video` (for MP4, MOV, M4V, WEBM). If the file extension is known and `kind=other`, the file extension will override `other` appropriately.
`is_public`|If true, file is public. Default false
`sha256`*|API will check the file's SHA256 checksum against this, and return an error if they do not match
`mime_type`|If the API cannot determine mime_type, it will use this
`{name}` + `_image_thumb_200s`|Key for custom derived thumbnail, 200 by 200 pixels, resized and cropped. If not included, API will try to create one, for images.
`{name}` + `_image_thumb_960r`|Key for custom derived thumbnail, within 640 width and 960 height. If an uploaded image has smaller proportions, one will not be created automatically.
`process_image_exif`*|If uploading a JPEG image with EXIF, and this is set to `0`, the API will not re-orient the image automatically.
`raw`|Embedded [raw values](/docs/implementation/raw).

* *If the API automatically rotates an image, the returned `sha256` will be different from the uploaded file.*


##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/files" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
  \"type\":\"com.example.site\",
  \"name\":\"That Thing!\",
  \"kind\":\"other\"
}" \
    -X POST \
    -H "X-Pretty-Json: 1"
```

Returns the created file details

```json
{
    "meta": {
        "code": 201
    },
    "data": {"...File Object..."}
}
```



## <span class="method method-patch">PATCH</span> /files/<span class="call-param">{file_id}</span> {#put-files-id .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">files</span>

Update a file's details.

If a file is ever made public, it could be accessed by others indefinitely using a previously-exposed `file_token_read`, or for a while after via the cache. To make a public file relatively secure again, delete it and upload it again as a new file.

### POST Body Data

Name|Description
-|-
`name`|256-character name or description (to be displayed and attached to the object)
`is_public`|True or false
`raw`|Embedded [raw values](/docs/implementation/raw). Not deleted unless explicitly set to empty values for each type.

### URL Parameters

Name|Description
-|-
`file_id`|ID of the file to update

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/files/73" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
  \"name\":\"butternut squash\"
}" \
    -X PUT \
    -H "X-Pretty-Json: 1"
```

Returns the updated file

```json
{
    "meta": {
        "code": 200
    },
    "data": {"...File Object..."}
}
```



## <span class="method method-put">PUT</span> /files/<span class="call-param">{file_id}</span>/content/<span class="call-param">{derived_key}</span> {#put-files-id-content-key .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">files</span>

Upload a new derivative file. You may only do this with an existing file placeholder (an incomplete file).

This is particularly useful if you want to include alternative versions of a file, such as different sizes of images, custom thumbnails instead of auto-generated thumbnails, or different music or video formats of a file.

### URL Parameters

Name|Description
-|-
`file_id`|ID of the file placeholder to create a derivative file for
`derived_key`|Multipart key to the file. Keys starting with `core_` are reserved. `core_image_200s` and `core_image_960r` can be set, but have to be 200x200 pixels and within 640x960 respectively, and the same mime type as `file_id`.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/files/69/content/core_image_200s" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns 204 on success

```json
-
```



## <span class="method method-put">PUT</span> /files/<span class="call-param">{file_id}</span>/content {#put-files-id-content .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">files</span>

Set a file placeholder's content. You may only do this with an incomplete file.

### URL Parameters

Name|Description
-|-
`file_id`|ID of the file to set contents for

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/files/75/content" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -F "content=@somethingtoupload.jpg" \
    -X PUT
```

Returns 204 on success

```json

```




## <span class="method method-delete">DELETE</span> /files/<span class="call-param">{file_id}</span> {#delete-files-id .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">files</span>

Delete a file. This will not disassociate a file with any other objects (posts, messages...).

### URL Parameters

Name|Description
-|-
`file_id`|ID of the file to delete

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/files/72" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X DELETE \
    -H "X-Pretty-Json: 1"
```

Returns the deactivated file

```json
{
    "meta": {
        "code": 200
    },
    "data": {"....File Object..."}
}
```