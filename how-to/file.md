### How To: File

Paid users are given 10GiB of file storage to upload to. Once files are uploaded, they can be attached to any object's Raw contents.


#### Uploading a File

Files can be uploaded in one or two steps.

* one `multipart/form-data` post including metadata and the file, or
* an initial post with metadata, and a second post with the file

##### A: Upload in a single step

To set the metadata and upload the file all at once, you must have a Content-Type of `multipart/form-data`, and keys for `name`, `kind`, `type`, and `content` (the file). The most common use will be for uploading images. You would want `kind=image`, and `type` will usually be a reverse domain name-style signature of the application uploading it (this will be searchable in the future).


##### B: Upload in two steps

If you want to provision an upload and set the metadata before uploading the file, you may.

Make a `POST` to `/files` of either `application/json` or `multipart/form-data` including a `name`, `kind`, and `type`. You may submit other [optional File parameters](../resources/files/lifecycle#post-files), as well. Then make a second `PUT` call using the created file's ID, to `/files/{file_id}/content`, with a `multipart/form-data` and a key set to `content` for the file.

If you upload in this way, then the first `POST` to `/files` will also return an `upload_parameters` key on the file, with `method` and `url` parameters for how to upload the file contents.


#### Derivative Images

When uploading GIF, JPEG, and PNG images, pnut will generate two standard resized images from your image: a 200x200 pixel thumbnail (`core_image_200s`) and a version that fits within 640 pixels wide by 960 tall, if the original image does not fit within those dimensions.

If you want to provide your own versions of those images, you can. To upload your own 200x200 pixel thumbnail, include it with the `core_image_200s` key, and be sure it is 200x200 pixels and GIF, JPEG, or PNG mime type. Likewise, upload a version with the key `core_image_960r`.

[Read more about derivative files](../resources/files/lifecycle#put-files-id-content-key)


#### Attaching Files to Objects

Once you have the ID of a completed image file, you can attach it to a post or message using the `io.pnut.core.oembed` *raw* type. You could fill in the oembed raw data as needed, but there are benefits to using a specialized "replacement" raw value for files, `+io.pnut.core.file`.

Here is an example of attaching a file to a post. The file has been uploaded, and returned the file object.

Using the `file_id` and the `file_token` from the newly uploaded file, we can attach it to an object. Using the convenient `+io.pnut.core.file` replacement raw type to attach it to a post, we can simply specify the format, and it will fill in the details from the file.

```bash
curl "https://api.pnut.io/v0/posts?include_post_raw=1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
    \"text\": \"#system of a duck\",
    \"raw\": [
  {
    \"type\": \"io.pnut.core.oembed\",
    \"value\": {
      \"+io.pnut.core.file\": {
        \"file_id\": ${POST_ID},
        \"file_token\": ${FILE_TOKEN},
        \"format\": \"oembed\"
      }
    }
  }
]" \
    -X POST
```

##### Public

If a file is ever made public, it could be accessed by others indefinitely using an embedded `file_token_read`, or until the file link expires, even if the file is later made private. For this reason, never imply in an app that a public file might be made secure by making it private again. Once someone has the file details, only deleting the file will restrict their access to it.


#### Linking to Files

##### Objects

On file objects themselves, `link` is a direct link to the file, and `link_short` redirects to the file, if it is a public file. `link` will expire after `link_expires_at`. To get a new link, GET `/files/{file_id}`, and it will have a new `link` and expiration time.

##### oEmbeds

If a post or message has a pnut.io file in a photo-type oEmbed raw item, it will have `url` link, with an expiration time in `url_expires_at`. `url` is always the most recent direct link to the file. If `url_expires_at` is past, then the file needs to be gotten again with the file read token (`GET /files/{file_id}?file_token_read=[file read token]`) or simply with an access token authorized with the files scope. This will refresh any `url` references to the file. The URLs expire in years, so a new one should very seldom be needed.

* Check if `url_expires_at` is passed
* Fetch the file with the `file_read_token` if it has expired. You will now have the `link` and `link_expires_at` from the file call, and can use that. Future requests to the file will be updated with the new link.

Non-photo oEmbed items have HTML elements rendered specific to the item.