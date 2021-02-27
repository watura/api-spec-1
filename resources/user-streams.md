# User Streams

User streams are long-lasting connections between the API and user-facing clients, for near-realtime interaction. They are similar to [App Streams](app-streams) but for individual users.

Look at [How To: User Streams](../how-to/user-streams) for details on usage.

Endpoints:

* [Delete a stream](#delete-users-me-streams-conn)
* [Delete a subscription](#delete-users-me-streams-conn-sub)


## <span class="method method-delete">DELETE</span> /users/me/streams/<span class="call-param">{connection_id}</span> {#delete-users-me-streams-conn .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Delete a user stream.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/me/streams/${CONNECTION_ID}" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X GET \
    -H "X-Pretty-Json: 1"
```

Returns 204.

```json
-
```


## <span class="method method-delete">DELETE</span> /users/me/streams/<span class="call-param">{connection_id}</span>/<span class="call-param">{subscription_id}</span> {#delete-users-me-streams-conn-sub .endpoint}

Token: <span class="endpoint-meta">user</span>

Scope: <span class="endpoint-meta">any</span>

Delete a subscription for a user stream.

##### Example {.example-code}

```bash
curl "https://api.pnut.io/v1/users/me/streams/${CONNECTION_ID}/${SUBSCRIPTION_ID}" \
    -H "Authorization: Bearer ${ACCESS_TOKEN}" \
    -X GET \
    -H "X-Pretty-Json: 1"
```

Returns 204.

```json
--
```