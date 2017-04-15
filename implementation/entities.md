### Entities

Entities are parsed on creation and update of objects.

Lengths and positions are using multibyte (UTF-32) code points. Notably, NSString and Javascript will not easily map to the same indices.


#### Links

An attempt is made after creation of posts to retrieve a `title` and `description` from any parsed links.

Inline and markdown links are parsed by the API by default. To not parse markdown links, set `entities.parse_markdown_links=0` in the POSTed JSON object. To not parse inline links, set `entities.parse_links=0`.

Field|Type|Description
-|-|-
`link`|string|The URL. If http/s was not specified, http will have been added.
`text`|string|The anchor text
`len`|integer|Length of the text
`pos`|integer|Position of text within the string
`title`|string|The retrieved title of `link` (optional)
`description`|string|The retrieved description of `link` (optional)


#### Mentions

Field|Type|Description
-|-|-
`id`|string|User ID
`len`|integer|Length of the mention
`pos`|integer|Position of the mention within the string
`text`|string|Username without the "at" symbol (`@`)
`is_leading`|boolean|If the mention comes before anything else in the string.
`is_copy`|boolean|If the mention comes immediately after a Forward slash (`/`), or another mention that does. If so, it will be subject to the user's Copy Mention notification preference.


#### Tags

Field|Type|Description
-|-|-
`len`|integer|Length of the tag
`pos`|integer|Position of the tag within the string
`text`|string|The tag without the pound/hash/number symbol (`#`)