# Raw


Raw data is arbitrary data that can be attached to posts, users, channels, messages, files, and polls. Clients can specify a `type` and a value for each item in the list of `raw` data.

Only specified types are verified by the server. Otherwise, clients will have to double-check the data to be sure clients that wrote them did so as expected. Any client can create any type of raw data, but as a developer, you can define a specification for your own type, and publicize what that is, so that other clients can also interpret it.

The total contents of the `raw` serialized JSON object can be up to 8192 bytes. Because items may already exist on mutable objects, you must check to make sure you will have space before adding to the existing data.

This is the format of a `raw` JSON object with a single item:

```json
"raw": {
  "TYPE_NAME": [
    {
      "YOUR_KEYS": "YOUR_DATA"
    }
  ]
}
```


## Core Types

Any `type` starting with `io.pnut.core` is checked by the server for validity, to an extent. Be sure to match their requirements when creating core channel types or `raw` data types.

If a submission is not valid, the whole operation will be prevented, and an error message will be returned in the `meta`.

Community-defined types and core types can be referenced on our [object-metadata GitHub repository](https://github.com/pnut-api/object-metadata).



## Inclusion

By default across the network, `raw` is not included on objects, and you must request it by setting query parameters:

* `include_raw=1`
* `include_user_raw=1`
* `include_channel_raw=1`
* `include_message_raw=1`
* `include_post_raw=1`
* `include_file_raw=1`
* `include_poll_raw=1`

If any relevant parameter is set to `1`, it will be included for the object and any children. It is preferable to not include something if you do not use it.



## Mutability &amp; Duplicates

Raw data attached to __posts__, __messages__, and __polls__ is *immutable*. It must be attached on creation of the object, and cannot be changed afterwards. Because they are immutable, they can have multiple raw items of the same type.

Channels, files, and users are mutable, and can only have one of a particular type. The `raw` data is still formed the same way, as a list for each type, even though there will only be a single item in the list, if it exists.



## Deleting Mutable Items

To delete a mutable item, include the `type` with an empty list, `[]`.



## Example

##### Example Post Creation {.example-code}

```bash
curl "https://api.pnut.io/v1/posts?include_post_raw=1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "Content-Type: application/json" \
    -d "{
  \"text\": \"I want everyone to know this is in English.\",
  \"raw\": {
    \"io.pnut.core.language\": [
      {
        \"language\": \"en\"
      }
    ]
  }
}"
    -X POST`
```

Returns the new post.

```json
{
  "meta": {
    "code": 201
  },
  "data": {
    "created_at": "2016-12-11T18:14:12Z",
    "id": "2384",
    "source": {
      "id": "3PFPMSet53RutGINA8e5HWqYg_UCDHad",
      "name": "Broadsword",
      "url": "http://xyz.s3rv.com"
    },
    "user": {"...User Object..."},
    "thread_id": "2384",
    "counts": {
      "bookmarks": 0,
      "reposts": 0,
      "replies": 0,
      "threads": 0
    },
    "content": {
      "html": "<span itemscope=\"https://pnut.io/schemas/Post\">I want everyone to know this is in English</span>",
      "text": "I want everyone to know this is in English",
      "entities": {
        "links": [],
        "mentions": [],
        "tags": []
      }
    },
    "you_bookmarked": false,
    "you_reposted": false,
    "raw": {
      "io.pnut.core.language": [
        {
          "language": "en"
        }
      ]
    }
  }
}
```