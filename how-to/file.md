# How To Upload and Attach Files

Paid users are given 10GiB of file storage to upload to. Invited users are given 512MiB. Once files are uploaded, they can be attached to any object's Raw contents.

* [Uploading a File](#uploading-a-file)
* [Derivative Images](#derivative-images)
* [Linking to Files](#linking-to-files)
 * [Directly](#linking-directly)
 * [Attached oEmbeds](#linking-with-oembeds)


## Uploading a File {#uploading-a-file}

Files can be uploaded in one or two steps:

### A: Upload in a single step *(recommended)*

1. Make one `multipart/form-data` POST including metadata and the file.

To set the metadata and upload the file all at once, you must have a Content-Type of `multipart/form-data`, and keys for `type`, and `content` (the file).

The most common use will be for uploading images. If you know you are uploading images only, you would want to set `kind=image`.

`type` will be searchable in the future, and is a file filter now.


### B: Upload in two steps

This takes an initial POST with metadata, and a second PUT with the file contents.

This allows you to provision an upload and set the metadata before uploading the file.

1. Make a `POST` to `/files` of either `application/json` or `multipart/form-data` including a `kind` and `type`. You may submit other [optional File parameters](../resources/files/lifecycle#post-files), as well.
2. Then make a second `PUT` call using the created file's ID, to `/files/{file_id}/content`, with a `multipart/form-data` and a key set to `content` for the file.

If you upload in this way, then the first `POST` to `/files` will also return an `upload_parameters` key on the file, with `method` and `url` parameters for how to upload the file contents.


## Derivative Images {#derivative-images}

When uploading GIF, JPEG, and PNG images, Pnut will generate two standard resized images from your image: a 200x200 pixel thumbnail (`core_image_200s`) and a version that fits within 640 pixels wide by 960 tall, if the original image does not fit within those dimensions.

If you want to provide your own versions of those images, you can. To upload your own 200x200 pixel thumbnail, include it with the `core_image_200s` key, and be sure it is 200x200 pixels and GIF, JPEG, or PNG mime type. Likewise, upload a version with the key `core_image_960r`.

[Read more about derivative files](../resources/files/lifecycle#put-files-id-content-key)



## Linking to Files {#linking-to-files}

### Directly {#linking-directly}

On file objects themselves, `url` is a direct link to the file, and if it is a public file, `url_short` is a redirect to the `url`.

#### Link Expiration

`url` will expire after `url_expires_at`. To get a new link, GET `/files/{file_id}`, and it will have a new `url` and expiration time.

`url_short` will always handle expired links.


### Attached oEmbeds {#linking-with-oembeds}

oEmbed is a standard way of adding file metadata to most Pnut objects &mdash; most commonly posts and messages.

`photo`-type oEmbeds provide data for displaying them properly. Non-photo oEmbed items have HTML elements rendered specific to the item in addition to metadata.


#### Attaching Images to Posts or Messages

Once you have the ID of a completed image file, you can attach it to a post or message using the `io.pnut.core.oembed` *raw* type. You could fill in the oEmbed raw data manually as needed, but it's highly recommended that you use this specialized "replacement" raw value for files: `+io.pnut.core.file`.

Below is an example of attaching an image file to a post. The file has already been uploaded, and returned the file object.

Using the `file_id` and the `file_token` from the newly uploaded file, we can attach it to an object. Using the convenient `+io.pnut.core.file` replacement raw type to attach it to a post, we can simply specify the format, and it will fill in the details from the file.

```bash
curl "https://api.pnut.io/v1/posts?include_post_raw=1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
    \"text\": \"system of a duck\",
    \"raw\": [
  {
    \"type\": \"io.pnut.core.oembed\",
    \"value\": {
      \"+io.pnut.core.file\": {
        \"file_id\": ${FILE_ID},
        \"file_token\": ${FILE_TOKEN},
        \"format\": \"oembed\"
      }
    }
  }
]" \
    -X POST
```

#### Public Access

If a file is ever made public and attached to an object, it could be accessed by others indefinitely using an embedded `file_token_read`, or until the file link expires, even if the file is later made private. For this reason, never imply in an app that a public file might be made secure by making it private again. Once someone has the file details, only deleting the file will restrict their access to it.

#### Link Expiration

If a post or message has a pnut.io file in a `photo`-type oEmbed raw item, it will have a `url` link, with an expiration time in `url_expires_at`. `url` is always the most recent direct link to the file. If `url_expires_at` is past, then the file needs to be retrieved again with the File Read Token (`GET /files/{file_id}?file_token_read={file read token}`) or simply with an access token authorized with the `files` scope (`GET /files/{file_id}`). This will refresh any `url` references to the file. The URLs expire in years, so a new one should very seldom be needed.

1. Check if `url_expires_at` is passed.
2. Fetch the file with the `file_read_token` if it has expired. You will now have a new `url` and `url_expires_at` from the file call, and can use that. Future requests to the file will be updated with the new link.

#### Video oEmbed

The API supports a Pnut-specific `video`-type oEmbed. When a file is submitted with `kind: video` it will be checked and certain parameters will be included in the oEmbed.

`.mov`, `.mp4`, `.m4p`, `.m4v`, or `.webm` extensions are expected, with `mime_type`s of `video/mp4`, `video/quicktime`, `video/x-msvideo`, or `video/webm`.

Provided metadata:

* __Always__ width
* __Always__ height
* __Always__ duration
* encoding (mov, mp4, webm...)
* frame_rate
* video_bitrate