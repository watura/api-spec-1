### Rate Limits

Every call to the API sends three return headers informing the rate limit. These limits vary based on whether the call is a `GET` or not and whether the call is authenticated or not.

Authenticated requests are limited on a per-token basis. Uauthenticated calls (no valid token is used) are limited based on the IP address used.

If a limit is hit, you must wait __600__ seconds before attempting again. The API will return an object with the seconds remaining in `meta.retry_in`, until it resets.

Here are the three return headers:

#### X-RateLimit-Limit

The number of hits to the attempted authentication and method combination allowed before a reset. These are the associated limits:

* Unauthenticated `GET` requests: 40
* Authenticated `GET` requests: 5000
* `POST`/`PUT`/`PATCH`/`DELETE`: 20


#### X-RateLimit-Remaining

The total number of hits to the attempted authentication and method combination available before the next reset.


#### X-RateLimit-Reset

Seconds remaining before a reset.

* Unauthenticated `GET` requests: 60 seconds
* Authenticated `GET` requests: 3600 seconds
* `POST`/`PUT`/`PATCH`/`DELETE`: 60 seconds