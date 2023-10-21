# System

Endpoints:

* [Get configuration](#get-sys-config)
* [Get status of an operation](#get-sys-ops-id)
* [Get statistics](#get-sys-stats)

The System endpoint gives access to system-wide information.


## <span class="method method-get">GET</span> /sys/config {#get-sys-config .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of parameters for interacting with the API.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/sys/config" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a catalog of parameters

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "file": {
            "audio_max_size_bytes": 52428800,
            "max_size_bytes": 104857600
        },
        "message": {
            "max_length": 2048
        },
        "post": {
            "max_length": 256,
            "seconds_between_duplicates": 60,
            "seconds_for_revision": 300
        },
        "rate_limit": {
            "anonymous": {
                "reads": 40,
                "read_reset_seconds": 60
            },
            "authorized": {
                "reads": 5000,
                "read_reset_seconds": 3600,
                "writes": 20,
                "write_reset_seconds": 60
            },
            "seconds_banned": 600
        },
        "raw": {
            "max_length": 8192
        },
        "user": {
            "description_max_length": 256,
            "name_max_length": 50,
            "presence_max_length": 100,
            "username_max_length": 20
        }
    }
}
```



## <span class="method method-get">GET</span> /sys/ops/<span class="call-param">{ops_id}</span> {#get-sys-ops-id .endpoint}

Scope: <span class="endpoint-meta">any</span>

Retrieve the status of a long-running operation.

Currently the only API call that creates a long-running operation is [deleting multiple files](/docs/resources/files/lifecycle#delete-files), type `FileDelete`.

`ended_at` will only be set if the operation has completed. `status` will be one of `running`, `dead`, and `completed`. `dead` is not definitive, but if `dead`, something went wrong.

### URL Parameters

Name|Description
-|-
`ops_id`|UUID of the operation to retrieve details for.

### Return Object Parameters

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
    </tr>
    <tr>
        <td><code>created_at</code></td>
        <td>string</td>
        <td>Time at which the operation was created, in ISO 8601 format; YYYY-MM-DDTHH:MM:SSZ.</td>
    </tr>
    <tr>
        <td><code>ended_at</code></td>
        <td>string</td>
        <td>Optional time at which the operation was completed, in ISO 8601 format; YYYY-MM-DDTHH:MM:SSZ.</td>
    </tr>
    <tr>
        <td><code>id</code></td>
        <td>string</td>
        <td>UUID that identifies the operation.</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>string</td>
        <td>Currently only <code>file_delete</code></td>
    </tr>
    <tr>
        <td><code>status</code></td>
        <td>string</td>
        <td>One of <code>running</code>, <code>dead</code>, <code>completed</code>.</td>
    </tr>
</table>

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/sys/ops/5c689c8d-5d59-4974-8705-f20b7abef338" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the status.

```json
{
    "data": {
        "created_at": "ISO-8601",
        "ended_at": "ISO-8601 (Optional)",
        "id": "UUID",
        "type": "String",
        "status": "String"
    },
    "meta": {
        "code": 200
    }
}
```



## <span class="method method-get">GET</span> /sys/stats {#get-sys-stats .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve basic statistics for the network.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/sys/stats" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of statistics

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "clients": {
            "created": 0,
            "public": 0
        },
        "days": 0,
        "files": {
            "created": 0
        },
        "messages": {
            "created": 0
        },
        "polls": {
            "created": 0
        },
        "posts": {
            "created": 0
        },
        "users": {
            "active": {
                "YYYY-MM-DD": 0
            },
            "created": 0,
            "disabled": 0,
            "present": 0
        }
    }
}
```
