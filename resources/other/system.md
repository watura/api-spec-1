# System

The System endpoint gives access to system-wide information.

Endpoints:

* [Get configuration](#get-sys-config)
* [Get statistics](#get-sys-stats)


## <span class="method method-get">GET</span> /sys/config {#get-sys-config .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of parameters for interacting with the API.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/sys/config" \
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
        "message": {
            "max_length": 2048
        },
        "post": {
            "max_length": 256,
            "repost_max_length": 256,
            "seconds_between_duplicates": 60
        },
        "rate_limit": {
            "anonymous": {
                "reads": 40,
                "seconds_between_reset": 60
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
            "username_max_length": 50
        }
    }
}
```



## <span class="method method-get">GET</span> /sys/stats {#get-sys-stats .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve basic statistics for the network.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/sys/stats" \
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
        "counts": {
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
            "posts": {
                "created": 0
            },
            "users": {
                "created": 0,
                "disabled": 0,
                "present": 0,
                "today": 0
            },
            "polls": {
                "created": 0
            }
        }
    }
}
```