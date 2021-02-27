# Entities

Entities are parsed on creation and update of objects. It's easiest to test outcomes using the [Text Processor endpoint](../resources/other/text-process).

Lengths and positions are using multibyte (UTF-32) code points. Notably, NSString and Javascript will not easily map to the same indices.

* [Example Content Object](#example-content)
* [Links](#links)
  * [Recognized TLDs](#recognized-tlds)
  * [Markdown Links](#markdown-links)
  * [URI Templates](#uri-templates)
* [Mentions](#mentions)
  * [Leading Mentions](#leading-mentions)
  * [Copy Mentions](#copy-mentions)
* [Tags](#tags)


## Example `content` Object {#example-content}

There are numerous objects in the API that use this pattern of object within them. The `content` object is used as a series of fields that help define a kind of "rich text", with links of different sorts and an HTML rendered version of text as well as indices for clients to build or parse the string more easily. Here is an example of the object:

```json
{
  "content": {
    "entities": {
      "links": [],
      "mentions": [],
      "tags": [
        {
          "len": 12,
          "pos": 126,
          "text": "quoteSunday"
        }
      ]
    },
    "html": "<span itemscope itemtype=\"https://pnut.io/schemas/Post\">So, West Virginia--my birth state--they changed the slogan on the interstate signs to \"Open for business\" for a while. -Ross\n\n<span data-tag-name=\"quoteSunday\" itemprop=\"tag\">#quoteSunday</span></span>",
    "text": "So, West Virginia--my birth state--they changed the slogan on the interstate signs to \"Open for business\" for a while. -Ross\n\n#quoteSunday"
  }
}
```


## Links {#links}

Field|Type|Description
-|-|-
`amended_len`|integer|The length of the `text` with the link's domain appended in brackets. Only included on markdown links.
`len`|integer|Length of the text
`pos`|integer|Position of text within the string
`text`|string|The anchor text
`title`|string|The title of `url` (only on markdown links with titles)
`url`|string|The URL. If a protocol was not specified, http will have been added. Accepted protocols are http/s, ftp, and gopher.

Inline and markdown links are parsed by the API by default.
To not parse markdown links, set `entities.parse_markdown_links=0` in the POSTed JSON object.
To not parse inline links, set `entities.parse_links=0`.

### Recognized TLDs {#recognized-tlds}

[A text file](https://pnut.io/dev-assets/tlds.txt) of the TLDs the API recognizes is available arranged for RegEx.

### Markdown Links {#markdown-links}

This is the format for creating a markdown link:
```markdown
[anchor text](https://example.com "optional title")
```
The example would be turned into `text`:
```markdown
anchor text [example.com]
```
and `html`:
```markdown
<a href="https://example.com" title="optional title">anchor text</a> [example.com]
```

#### Markdown link length calculation

When markdown links are included in a Post or Message, the "length" of the Post or Message is calculated taking these things into consideration:

* The `text` length of the link (inside the brackets) is counted against the total text length
* The `url` and `title` lengths (inside the parentheses) do not count against the total length
* When the `text` is the same as the *host/domain* of the `url`, the domain is not appended after the link
 * `[pnut.io](pnut.io/docs)` becomes `<a href="http://pnut.io/docs">pnut.io</a>` with a length of `7`
* When the domain *is* appended after the link, the domain does not count against the total length.
 * `[text](pnut.io/docs)` becomes `<a href="http://pnut.io/docs">text</a> [pnut.io]` with a length of `4`


### URI Templates {#uri-templates}

When creating a post or message, you can signal to the API to replace the literal text `{object_id}` in links with the newly created post or message's ID.

For example, a post with this text:
```markdown
link to this very post: https://posts.pnut.io/{object_id}
```
will become:
```markdown
link to this very post: https://posts.pnut.io/58399
```


## Mentions {#mentions}

Field|Type|Description
-|-|-
`id`|string|User ID
`is_copy`|boolean|If the mention comes immediately after a Forward Slash (`/`), or another mention that does. If so, it will be subject to the user's Copy Mention notification preference. Only included if true.
`is_leading`|boolean|If the mention comes before any other text in the string. Only included if true.
`len`|integer|Length of the mention
`pos`|integer|Position of the mention within the string
`text`|string|Username without the "at" symbol (`@`)

### Leading Mention Examples {#leading-mentions}

All of these are leading mentions:
```markdown
@bazbt3 spam?
```
```markdown
@akulbe @jws Interestingly, I have absolutely no idea where I uploaded that. 😜
```
```markdown
>~-> @ugum1 yo!
```

### Copy Mentions {#copy-mentions}

A copy mention is a way of copying someone on a post without being as direct as a leading mention or even a regular mention. Usually a person will end their post with `/@user` to add it to their mentions, but without immediacy.

All the mentions in this example are copy mentions:
```markdown
Our Community Wiki Patter Chat room is open! Submit ideas, suggestions, praise, problems… ;)

/@33MHz @blumenkraft @jcoder 
```


## Tags {#tags}

Tags are `#` directly in front of a string of characters. They link content to other uses of the same tag. This helps connect people with similar interests.

Tags can have emoji, numbers, `_`, and letters in different languages.

Tag lookups are normalized lowercase with underscores (`_`) removed. They still will show in the `html` and `text` of an object however they were written, but the linking ignores them. So a post with the tag `#the_lost_children` will be linked to any other posts with the tag `#theLostChildren`, `#thelostchildre_n`, etc.

Pnut doesn't recognize tags that are just numbers.

Field|Type|Description
-|-|-
`len`|integer|Length of the tag
`pos`|integer|Position of the tag within the string
`text`|string|The tag without the hash symbol (`#`)