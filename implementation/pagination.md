# Pagination


Paginated calls will include a `pagination_id` on the paginated objects.

The `meta` object in the returned JSON will also have a `min_id` and `max_id`.

Objects are always returned in reverse chronological order (newest first).

Pagination parameters can be used in conjunction with [stream markers](../resources/stream-marker) on some calls.


## Before and since

You may append a query parameter of `since_id={ID}`, which will then only return objects higher than that ID.

A query parameter of `before_id={ID}` dictates that the objects will be lower than that ID.

They may be used in conjunction.

## Count

By default, up to 20 of an object will be returned. A query parameter of `count={N}` can override that. `count` can be `1` to `200` or `-200` to `-1`. If it is invalid, the API will ignore it.

Negative `count` can be used on most streams.

Positive will return the newest. Negative will return the oldest.


## Examples

In these examples, `50` is the most recent post ID.

### Oldest since

This can be used if you do not want to miss posts since your last request. It will get the oldest 20 posts after `4`.

```markdown
https://api.pnut.io/v1/posts/streams/global
  ?since_id=4
  &count=-20
```
Returns posts `24`-`5`.

### Newest since

This will skip some posts, because it is getting the 20 newest posts after `4`. You may want to do this, if you want to skip to the latest without retrieving any you already have.

```markdown
https://api.pnut.io/v1/posts/streams/global
  ?since_id=4
```
Returns posts `50`-`31`.

### Newest before

```markdown
https://api.pnut.io/v1/posts/streams/global
  ?before_id=6
  &count=4
```
Returns posts `5`, `4`, `3`, `2`.

### Newest within a range

```markdown
https://api.pnut.io/v1/posts/streams/global
  ?since_id=4
  &before_id=6
```
Returns post `5`.