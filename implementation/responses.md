### Responses

All API endpoints listed under Resources, whether successful or not, will be returned in the same type of envelope structure.

*The [authentication endpoints](../authentication/overview) return a slightly different format that follows the OAuth2 specification.*


#### Response Envelope

The top-level response is an object containing two keys. The first key, `data`, corresponds to the actual response item requested. This may either be an object itself or a list of objects. The particular data returned is described in each endpoint's documentation. If the request is unsuccessful (results in an error), no `data` key will be present.

The second key present, `meta`, corresponds to an object containing additional information about the request. This object will always contain `code`, a copy of the HTTP status code that has been returned. It will also contain [pagination metadata](pagination) and/or a [stream marker](../resources/stream-marker) when relevant.

##### Sample Response Envelope
```json
{
    "data": "the data you requested",
    "meta": {
        "more": true,
        "max_id": "2703",
        "min_id": "2702",
        "marker": {
            "id": "2593",
            "last_read_id": "5719",
            "percentage": "0",
            "updated_at": "2017-12-26T15:26:19Z",
            "version": "YM-fTQk8_0nsdlI01kcUCGvyvHN",
            "name": "global"
        },
        "code": 200
    }
}
```


#### CORS

[CORS](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing) is supported for authenticated cross-domain API requests direct from browsers. Be sure to carefully consider how your app will handle access tokens for CORS requests.



#### X-Pretty-Json Header

The examples in the documentation include the `X-Pretty-Json` header. This prints the JSON with more readable spacing, for testing. In production there's no reason to include it. If it is set at all, the JSON will be returned that way.



#### Errors

If the request was unsuccessful, no `data` key will be returned. `code` and `error_message` keys will indicate what error occurred. There may also be a uniquely-identifying `error_id` present that can be helpful when talking to pnut.io support.

The API will respond with some accuracy for almost all issues. There are two unspecific errors: you may receive `code: 400, error_message: Wrong type`, which should be straight forward to determine the cause from the client. If you receive `code: 500, error_message: Internal Server Error`, something internal failed and it should be immediately reported to support.



#### HTTP status codes

Pnut.io uses the HTTP status code to indicate if an API request was a success or failure. For environments that can't access the raw HTTP response directly, this value is also duplicated in the `meta.code` value. The following table lists all currently used HTTP status codes. If you get a status code that is not documented below, please [open an issue](https://github.com/pnut-api/api-spec/issues).

<table>
    <thead>
        <tr>
            <th>Code</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>200 OK</code></td>
            <td>The request was successful.</td>
        </tr>
        <tr>
            <td><code>204 No Content</code></td>
            <td>Returned when retrieving an incomplete file or when uploading file content to an incomplete file.</td>
        </tr>
        <tr>
            <td><code>302 Found</code></td>
            <td>Redirection to the final destination of a resource. Returned when retrieving <a href="../resources/users/profile#get-users-id-avatar">user avatar</a>, or a <a href="../resources/users/profile#get-users-id-cover">cover image</a>.</td>
        </tr>
        <tr>
            <td><code>400 Bad Request</code></td>
            <td>The API request was malformed in some way. A message should be returned that indicates how this request can be fixed.</td>
        </tr>
        <tr>
            <td><code>401 Unauthorized</code></td>
            <td>A token is required. If you passed a token, a message should indicate why this token is not authorized.</td>
        </tr>
        <tr>
            <td><code>403 Forbidden</code></td>
            <td>The token you are providing doesn't have the right to perform the request. Please check that your token is of the correct type and has the <a href="../authentication/scope">required scope</a>.</td>
        </tr>
        <tr>
            <td><code>404 Not Found</code></td>
            <td>The requested resource was not found.</td>
        </tr>
        <tr>
            <td><code>429 Too Many Requests</code></td>
            <td>The request could not be completed due to a <a href="rate-limits/">rate limit</a>. Please wait at the number of seconds specified in the <code>Retry-After</code> header before you retry this request.</td>
        </tr>
        <tr>
            <td><code>500 Internal Server Error</code></td>
            <td>An unexpected server error has occurred. Talk to pnut.io support to solve the issue.</td>
        </tr>
        <tr>
            <td><code>507 Insufficient Storage</code></td>
            <td>The request couldn't be completed because the authorized user has hit a quota limit. This could be returned when trying to <a href="../resources/files/lifecycle#post-files">upload a file</a>. The <a href="../resources/token#get-token">current token information</a>'s <code>data.storage.available</code> key can help an app avoid this error.</td>
        </tr>
    </tbody>
</table>
