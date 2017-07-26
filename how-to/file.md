### How To File

Paid users are given 10GiB of file storage to upload to. Once files are uploaded, they can be attached to any object's Raw contents.


#### Uploading a File

Files can be uploaded in one or two steps.

* one `multipart/form-data` post including metadata and the file, or
* an initial post with metadata, and a second post with the file

##### A: Upload in a single step

To set the metadata and upload the file all at once, you must have a Content-Type of `multipart/form-data`, and keys for `name`, `kind`, `type`, and `content` (the file). The most common use will be for uploading images. You would want `kind=image`, and `type` will usually be a reverse domain name-style signature of the application uploading it (this will be searchable in the future).


##### B: Upload in two steps

If you want to provision an upload and set the metadata before uploading the file, you may.

Make a `POST` to `/files` with either JSON or `multipart/form-data` including a `name`, `kind`, and `type`. You may submit other optional parameters, as well. Then make a second `PUT` call using the created file's ID, to `/files/{file_id}/content`, with a `multipart/form-data` and a key set to `content` for the file.

If you upload in this way, then the first `POST` to `/files` will also return an `upload_parameters` key on the file, with `method` and `url` parameters for how to upload the file contents.


#### Attaching Files to Objects

Once you have the ID of a completed file, you can attach it to a post or message using the `io.pnut.core.oembed` *raw* type. You can simply fill in the oembed raw data as needed, or you can use a specialized "replacement" raw value for files, `+io.pnut.core.file`.

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