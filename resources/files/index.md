### Files



##### Click For Example [<i class="fa fa-paragraph" aria-hidden="true"></i>](#file) {#file .endpoint}

```json
{
  "raw": [],
  "is_complete": true,
  "created_at": "2016-10-25T14:53:54Z",
  "id": "5761572",
  "image_info": {
    "height": 2448,
    "width": 2448
  },
  "kind": "image",
  "mime_type": "image/jpeg",
  "name": "IMG_20161025_095315.jpg",
  "pagination_id": "5761572",
  "is_public": false,
  "sha256": "6ca4ecf3645ae3d04de0682e65e9d330a47dfb37",
  "size": 1079303,
  "source": {
    "client_id": "gM5cMMBD7JJ6xamnBTcbhzkDCnR7xAux",
    "link": "http://robinapp.net",
    "name": "Robin"
  },
  "type": "robin.image.photo",
  "link": "https://d36tc8clsz1tk5.cloudfront.net/adn-uf-01/o-/O1/TG/o-O1TGXChj9yYa6R5p-v8ypgPRqhZ-qlSirqlMVSczc?response-cache-control=public%2C%20max-age%3D7200%2C%20s-maxage%3D172800&response-content-disposition=inline%3B%20filename%2A%3DUTF-8%27%27IMG_20161025_095315.jpg&Expires=1489827600&Signature=miDIsZr4OPwQx8gURcr3G8fDg8igSC2FupJYuqyxAoecb9NQszmZ5GqlWjgWY8-9pbdVpau5fNf~0bN78a9eSX6z3ieXI9KwX~jC1nI6ojrdCNOfQOEH8H~CGhYJETN24GCsQ7Q7TpgK3KFBeLrMz2dK~vv~hyGvmf-n6zm4mu0_&Key-Pair-Id=APKAIWNGPWT6YVKFBWJA",
  "link_expires": "2017-03-18T09:00:00Z",
  "user": {...}
},
```

#### Fields [<i class="fa fa-paragraph" aria-hidden="true"></i>](#file-fields) {#file-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
    </tr>

    <tr>
        <td><code>created_at</code></td>
        <td>string</td>
        <td>The time at which the file was created in ISO 8601 format.</td>
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
        <td>Valid options are <code>image</code> and <code>other</code>. <code>image</code>-type must have a Content-Type of <code>image/png</code>, <code>image/gif</code>, or <code>image/jpeg</code> or <code>image/jpg</code>.</td>
    </tr>

    <tr>
        <td><code>link</code></td>
        <td>string</td>
        <td>Direct link to the file, but with an expiration. After expiration, file object will need to be fetched to get a new link (<code>GET /files/{file_id}</code>).</td>
    </tr>

    <tr>
        <td><code>link_expires_at</code></td>
        <td>string</td>
        <td>ISO 8601 timestamp of when <code>link</code> will expire.</td>
    </tr>

    <tr>
        <td><code>link_short</code></td>
        <td>string</td>
        <td>A redirect link to the file. Only included if <code>is_public</code>.</td>
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
        <td>Included on creation of a file placeholder.
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
        <td><code>user</code></td>
        <td>object</td>
        <td>This is an embedded User object. In certain cases, this key may be omitted.</td>
    </tr>
</table>


#### General File Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#general-file-parameters) {#general-file-parameters}

Any endpoint that returns file objects can be subject to these parameters.

##### General Parameters

Name|Type|Description
-|-|-
`include_incomplete`|integer (0 or 1)|Include incomplete files. Only applicable to the user's file stream. Defaults to true.
`include_private`|integer (0 or 1)|Include private files. Only applicable to the user's file stream. Defaults to true.
`file_types`|string|Comma-separated list of file types to retrieve. Only applicable to the user's file stream. If not included, will return any files the app is authorized to view.
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects. Defaults to false.
`include_file_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all file objects. Defaults to false.