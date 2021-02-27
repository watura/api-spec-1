# Files


* [File Fields](#file-fields)
* [General File Parameters](#general-file-parameters)
* [Mime Types](#mime-types)


## File Fields {#file-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
    </tr>
    <tr>
        <td><code>audio_info</code></td>
        <td>object</td>
        <td>Included if <code>kind: audio</code>.
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>
                <tr>
                    <td><code>duration</code></td>
                    <td>integer</td>
                    <td>Length of audio in seconds.</td>
                </tr>
                <tr>
                    <td><code>duration_string</code></td>
                    <td>string</td>
                    <td>Length of audio in hour:minute:second format. Only included on files since API 0.9.5.</td>
                </tr>
                <tr>
                    <td><code>bitrate</code></td>
                    <td>integer</td>
                    <td>Bitrate in kbps.</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>created_at</code></td>
        <td>string</td>
        <td>The time at which the file was created in ISO 8601 format; YYYY-MM-DDTHH:MM:SSZ.</td>
    </tr>
    <tr>
        <td><code>file_token</code></td>
        <td>string</td>
        <td>A token to modify the file. Only included on creation, if included in the query string, or if the Files scope gives you access to the file.</td>
    </tr>
    <tr>
        <td><code>file_token_read</code></td>
        <td>string</td>
        <td>A token to access the file. Only included if <code>is_public</code> or if it is included in the query string.</td>
    </tr>
    <tr>
        <td><code>id</code></td>
        <td>string</td>
        <td>Primary identifier for a file. This will be an integer, but it is always expressed as a string to avoid limitations with the way JavaScript integers are expressed. This id space is unique to file objects. There can be a Post and User with the same ID; no relation is implied.</td>
    </tr>
    <tr>
        <td><code>image_info</code></td>
        <td>object</td>
        <td>Included if <code>kind: image</code>.
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>
                <tr>
                    <td><code>height</code></td>
                    <td>integer</td>
                    <td>Height of the image.</td>
                </tr>
                <tr>
                    <td><code>width</code></td>
                    <td>integer</td>
                    <td>Width of the image.</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>is_complete</code></td>
        <td>boolean</td>
        <td>Whether file is a placeholder, or the contents have been uploaded.</td>
    </tr>
    <tr>
        <td><code>is_public</code></td>
        <td>boolean</td>
        <td>Whether file is public or private. If private, it still may be attached to a public object, such as a post.</td>
    </tr>
    <tr>
        <td><code>kind</code></td>
        <td>string</td>
        <td>Valid options are <code>audio</code>, <code>video</code>, <code>image</code>, and <code>other</code>. <code>audio</code> is currently limited to 52428800-byte files (32MiB). See <a href="#mime-types">Mime Types</a> for explanation.</td>
    </tr>
    <tr>
        <td><code>url</code></td>
        <td>string</td>
        <td>Direct link to the file, but with an expiration.</td>
    </tr>
    <tr>
        <td><code>url_expires_at</code></td>
        <td>string</td>
        <td>ISO 8601 timestamp of when <code>url</code> will expire; YYYY-MM-DDTHH:MM:SSZ. After expiration, file object will need to be fetched to get a new link (<code>GET /files/{file_id}</code>, this also refreshes any derivative files).</td>
    </tr>
    <tr>
        <td><code>url_short</code></td>
        <td>string</td>
        <td>A redirect link to the file. Only included if <code>is_public</code>.</td>
    </tr>
    <tr>
        <td><code>mime_type</code></td>
        <td>string</td>
        <td>Optional. Mime encoding of the file. See <a href="#mime-types">Mime Types</a> for details.</td>
    </tr>
    <tr>
        <td><code>name</code></td>
        <td>string</td>
        <td>A readable name of the file. Can be used descriptively or not. Up to 256 Unicode characters.  <em>Be sure to escape if necessary.</em></td>
    </tr>
    <tr>
        <td><code>sha256</code></td>
        <td>string</td>
        <td>sha256 checksum of file</td>
    </tr>
    <tr>
        <td><code>size</code></td>
        <td>integer</td>
        <td>Size of the file in bytes.</td>
    </tr>
    <tr>
        <td><code>source</code></td>
        <td>object</td>
        <td>An embedded object of the client that created the file.</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>string</td>
        <td>The type of file. Generally uses a reversed domain name to identify the intended purpose. Non-core file types (<code>io.pnut.core.*</code>) are not authenticated by the server; clients should not assume other clients created their file types the same way.</td>
    </tr>
    <tr>
        <td><code>upload_parameters</code></td>
        <td>object</td>
        <td>Only included on creation of a file placeholder.
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>
                <tr>
                    <td><code>method</code></td>
                    <td>string</td>
                    <td>e.g., <code>post</code></td>
                </tr>
                <tr>
                    <td><code>url</code></td>
                    <td>string</td>
                    <td>URL to upload the file to</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>derivative_files</code></td>
        <td>object</td>
        <td>Up to 10 derivative files. The keys can be anything, though keys starting with <code>core_</code> are reserved. Reserved keys are allowed if they match specified parameters. For example:
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>
                <tr>
                    <td><code>core_image_200s</code></td>
                    <td>object</td>
                    <td>
                        <table>
                            <tr>
                                <th>Field</th>
                                <th>Type</th>
                                <th>Description</th>
                            </tr>
                            <tr>
                                <td><code>url</code></td>
                                <td>string</td>
                                <td>Direct link to the file, but with an expiration.</td>
                            </tr>
                            <tr>
                                <td><code>url_expires_at</code></td>
                                <td>string</td>
                                <td>ISO 8601 timestamp of when <code>url</code> will expire; YYYY-MM-DDTHH:MM:SSZ. After expiration, <code>GET /files/{file_id}</code> of the derived file will refresh these as well.</td>
                            </tr>
                            <tr>
                                <td><code>mime_type</code></td>
                                <td>string</td>
                                <td>The mime-encoding of the file.</td>
                            </tr>
                            <tr>
                                <td><code>name</code></td>
                                <td>string</td>
                                <td>A readable name of the file. Can be used descriptively or not. Up to 255 ASCII characters.</td>
                            </tr>
                            <tr>
                                <td><code>sha256</code></td>
                                <td>string</td>
                                <td>sha256 checksum of file</td>
                            </tr>
                            <tr>
                                <td><code>size</code></td>
                                <td>integer</td>
                                <td>Size of the file in bytes.</td>
                            </tr>
                            <tr>
                                <td><code>image_info</code></td>
                                <td>object</td>
                                <td>Included if <code>kind: image</code>.
                                    <table>
                                        <tr>
                                            <th>Field</th>
                                            <th>Type</th>
                                            <th>Description</th>
                                        </tr>
                                        <tr>
                                            <td><code>height</code></td>
                                            <td>integer</td>
                                            <td>Height of the image.</td>
                                        </tr>
                                        <tr>
                                            <td><code>width</code></td>
                                            <td>integer</td>
                                            <td>Width of the image.</td>
                                        </tr>
                                    </table>
                                </td>
                            </tr>
                        </table>
                    </td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>user</code></td>
        <td>object</td>
        <td>This is an embedded User object. In certain cases, this key may be omitted.</td>
    </tr>
    <tr>
        <td><code>user_id</code></td>
        <td>string</td>
        <td>Primary identifier for the user who created the file. This is only included if the <code>user</code> above is omitted.</td>
    </tr>
    <tr>
        <td><code>video_info</code></td>
        <td>object</td>
        <td>Included if <code>kind: video</code>.
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>
                <tr>
                    <td><code>duration</code></td>
                    <td>integer</td>
                    <td>Length of video in seconds.</td>
                </tr>
                <tr>
                    <td><code>duration_string</code></td>
                    <td>string</td>
                    <td>Length of video in hour:minute:second format.</td>
                </tr>
                <tr>
                    <td><code>bitrate</code></td>
                    <td>integer</td>
                    <td>Bitrate in kbps.</td>
                </tr>
                <tr>
                    <td><code>height</code></td>
                    <td>integer</td>
                    <td>Height of the video.</td>
                </tr>
                <tr>
                    <td><code>width</code></td>
                    <td>integer</td>
                    <td>Width of the video.</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>raw</code></td>
        <td>object</td>
        <td>The raw items attached to this object. Only included if query parameter specified.
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>
                <tr>
                    <td><code>{type name}</code></td>
                    <td>list</td>
                    <td>A list of objects of this type.</td>
                </tr>
            </table>
        </td>
    </tr>
</table>


## General File Parameters {#general-file-parameters}

Any endpoint that returns file objects can be subject to these parameters.

### General Parameters

Name|Type|Description
-|-|-
`include_incomplete`|integer (0 or 1)|Include incomplete files. Only applicable to the user's file stream. Defaults to true.
`include_private`|integer (0 or 1)|Include private files. Only applicable to the user's file stream. Defaults to true.
`mime_types`|list|Comma-separated list of mime types to retrieve. Only applicable to the user's file stream.
`file_types`|string|Comma-separated list of file types to retrieve. Only applicable to the user's file stream. If not included, will return any files the app is authorized to view.
`exclude_file_types`|string|Comma-separated list of file types not to retrieve. Only applicable to the user's file stream. Ignored if `file_types` set.
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects. Defaults to false.
`include_file_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all file objects. Defaults to false.


## Mime Types {#mime-types}

`kind` and `mime_type` must be coordinated.

Both are optional when uploading a file in one step.

If creating a file placeholder and uploading later, `kind` is required on creation, and `mime_type` is optional on file upload.

* If you specify both, it will return an error if they do not match.
* If you do not specify either, the API will interpret `mime_type` and assign `kind` based on what it finds.
* If you only specify `kind`, the API will interpret `mime_type` and return an error if they do not match.
* If you only specify `mime_type`, the API will assign `kind` based on `mime_type`.

Multiple mime types are accepted for some file types, but they will be normalized and recorded as a single mime type listed in the charts below.

### File Encoding

If the included `mime_type` matches any of the following, its text encoding will attempt to be detected by the server (i.e., for UTF-8 encoding):

* `text/{anything}`
* `application/msword`
* `application/vnd.oasis.opendocument.text`
* `application/rtf`
* `application/xml`
* `application/json`
* `application/javascript`

### Audio

Files with `kind: audio` must have the following `mime_type`:

File Type|`mime_type`|Also accepted
-|-|-
MP3|audio/mpeg|audio/mp3
MP4|audio/mp4|audio/m4a, audio/x-m4a
WAVE|audio/wave|audio/wav, audio/x-wav, audio/x-pn-wav
FLAC|audio/flac|audio/x-flac

### Video

Files with `kind: video` must have the following `mime_type`:

File Type|`mime_type`|Also accepted
-|-|-
MP4|video/mpeg|video/quicktime, video/m4v, video/x-m4v, video/mp4
WEBM|video/webm|-

### Image

Files with `kind: image` must have the following `mime_type`:

File Type|`mime_type`|Also accepted
-|-|-
PNG|image/png|-
JPEG|image/jpeg|image/jpg
GIF|image/gif|-