### Pagination


Paginated calls will include a `pagination_id` on the paginated objects.

The `meta` key in the returned JSON will also have a `min_id` and `max_id`.

Objects are always returned in reverse chronological order (newest first).

You may append a query parameter of `since_id={ID}`, which will then only return objects higher than that ID. A query parameter of `before_id={ID}` dictates that the objects will be lower than that ID. They may be used in conjunction.


Here are some examples, where `8` happens to be the most recent post ID:

```bash
/posts/streams/global
  ?since_id=4
```
Returns posts `8,7,6,5`.

```bash
/posts/streams/global
  ?before_id=6
  &count=4
```
Returns posts `5,4,3,2`.

```bash
/posts/streams/global
  ?since_id=4
  &before_id=6
  &count=4
```
Returns post `5`.


Pagination parameters can be used in conjunction with [stream markers](../resources/stream-marker) on some calls.