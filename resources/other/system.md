### System

The System endpoint gives access to system-wide information.


#### <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /sys/config [<i class="fas fa-paragraph"></i>](#get-sys-config) {#get-sys-config .endpoint}

Retrieve a list of parameters for interacting with the API.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/sys/config" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a catalog of parameters

```json
"call for example 1"
```



#### <span class="endpoint-meta"><i class="fas fa-unlock"></i> none</span><span class="method method-get">GET</span> /sys/stats [<i class="fas fa-paragraph"></i>](#get-sys-stats) {#get-sys-stats .endpoint}

Retrieve basic statistics for the network.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/sys/stats" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of statistics

```json
"call for example 2"
```