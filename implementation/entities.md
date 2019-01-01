# Entities

Entities are parsed on creation and update of objects. It's easiest to test outcomes using the [Text Processor endpoint](../resources/other/text-process).

Lengths and positions are using multibyte (UTF-32) code points. Notably, NSString and Javascript will not easily map to the same indices.


## Links

Field|Type|Description
-|-|-
`amended_len`|integer|The length of the `text` with the link's domain appended in brackets (only included on markdown links)
`link`|string|The URL. If http/s was not specified, http will have been added.
`text`|string|The anchor text
`len`|integer|Length of the text
`pos`|integer|Position of text within the string
`title`|string|The title of `link` (only on markdown links with titles)

Inline and markdown links are parsed by the API by default.
To not parse markdown links, set `entities.parse_markdown_links=0` in the POSTed JSON object.
To not parse inline links, set `entities.parse_links=0`.

### Markdown Links {#markdown-links}

This is the format for creating a markdown link:
```
[anchor text](https://example.com "optional title")
```
The example would be turned into `text`:
```
anchor text [example.com]
```
and `html`:
```
<a href="https://example.com" title="optional title">anchor text</a> [example.com]
```

### URI Templates {#uri-templates}

When creating a post or message, you can signal to the API to replace the literal text `{object_id}` in links with the newly created post or message's ID.

For example, a post with this text:
```
link to this very post: https://posts.pnut.io/{object_id}
```
will become:
```
link to this very post: https://posts.pnut.io/58399
```


## Mentions

Field|Type|Description
-|-|-
`id`|string|User ID
`is_copy`|boolean|If the mention comes immediately after a Forward Slash (`/`), or another mention that does. If so, it will be subject to the user's Copy Mention notification preference.
`is_leading`|boolean|If the mention comes before anything else in the string.
`len`|integer|Length of the mention
`pos`|integer|Position of the mention within the string
`text`|string|Username without the "at" symbol (`@`)

### Leading Mention Examples {#leading-mentions}

All of these are leading mentions:
```
@bazbt3 spam?
```
```
@akulbe @jws Interestingly, I have absolutely no idea where I uploaded that. 😜
```
```
>~-> @ugum1 yo!
```

### Copy Mentions {#copy-mentions}

A copy mention is a way of copying someone on a post without being as direct as a leading mention or even a regular mention. Usually a person will end their post with `/@user` to add it to their mentions, but without immediacy.

All the mentions in this example are copy mentions:
```
Our Community Wiki Patter Chat room is open! Submit ideas, suggestions, praise, problems… ;)

/@33MHz @blumenkraft @jcoder 
```


## Tags

Tags are `#` directly in front of a string of characters. They link content to other uses of the same tag. This helps connect people with similar interests.

Tags can have emoji, numbers, `_`, and letters in different languages.

Tag lookups are normalized lowercase with underscores (`_`) removed. They still will show in the `html` and `text` of an object however they were written, but the linking ignores them. So a post with the tag `#the_lost_children` will be linked to any other posts with the tag `#theLostChildren`, `#thelostchildre_n`, etc.

Pnut doesn't recognize tags that are just numbers. 

Field|Type|Description
-|-|-
`len`|integer|Length of the tag
`pos`|integer|Position of the tag within the string
`text`|string|The tag without the hash symbol (`#`)