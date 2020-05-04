# Badges

Badges are accessible to users who are [current badge holders](https://pnut.io/about/resources/sign-up).

A user can set what badge to display on their profile [from their account](https://pnut.io/account/badge), or a client can update it [by updating the user](https://docs.pnut.io/resources/users/profile).

Endpoints:

* [Get a badge](#get-badges-id)
* [Get all badges](#get-badges)
* [Get the authenticated user's badges](#get-users-me-badges)


## <span class="method method-get">GET</span> /badges/<span class="call-param">{badge_id}</span> {#get-badges-id .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a badge object.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/badges/1" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns the badge object

```json
{
    "meta": {
        "code": 200
    },
    "data": {
        "id": "0",
        "name": "String",
        "description": "String"
    }
}
```


## <span class="method method-get">GET</span> /badges {#get-badges .endpoint}

Scope: <span class="endpoint-meta">none</span>

Retrieve a list of all badges. It is not paginated.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/badges" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of badges

```json
{
    "meta": {
        "code": 200
    },
    "data": [
        {
            "id": "0",
            "name": "String",
            "description": "String"
        }
    ]
}
```


## <span class="method method-get">GET</span> /users/me/badges {#get-users-me-badges .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Retrieve a list of all badges for the authenticated user. It is not paginated.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v0/users/me/badges" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -H "X-Pretty-Json: 1"
```

Returns a list of badges in order of most recently awarded.

```json
{
    "meta": {
        "code": 200
    },
    "data": [
        {
            "id": "0",
            "name": "String",
            "description": "String",
            "awarded_at": "ISO 8601"
        }
    ]
}
```