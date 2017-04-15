### Sys

The System endpoint gives access to system-wide information.


#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /sys/config [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-sys-config) {#get-sys-config .endpoint}

Retrieve a list of parameters for interacting with the API.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/sys/config" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
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
      "seconds_between_duplicates": 120
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
    "user": {
      "description_max_length": 256,
      "username_max_length": 50
    }
  }
}
```



#### <span class="endpoint-meta"><i class="fa fa-unlock" aria-hidden="true"></i> none</span><span class="method method-get">GET</span> /sys/stats [<i class="fa fa-paragraph" aria-hidden="true"></i>](#get-sys-stats) {#get-sys-stats .endpoint}

Retrieve basic statistics for the network.

##### Example Call {.example-code}

```bash
curl "https://api.pnut.io/v0/sys/stats" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}"
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
        "created": 49
      },
      "days": 92,
      "posts": {
        "created": 58390
      },
      "messages": {
        "created": 482
      },
      "users": {
        "created": 156,
        "disabled": 2,
        "present": 12
      }
    }
  }
}
```