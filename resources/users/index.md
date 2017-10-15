### Users



#### General User Identifiers [<i class="fa fa-paragraph" aria-hidden="true"></i>](#general-user-identifiers) {#general-user-identifiers}

Unless otherwise specified, user identifiers can be any of the following:

* User ID (`1`)
* @username (`@33mhz`)
* "me", when authenticated

User IDs are preferred where convenient, because they take less effort and will never change (unlike usernames).

Referring to usernames is not case-sensitive, but usernames will be returned from the API with the casing specified by the user -- so comparisons should normalize them before comparing.



#### Canonical User Profiles

Any user profile can be found at `https://pnut.io/@username`.


#### Object

##### Click For Example [<i class="fa fa-paragraph" aria-hidden="true"></i>](#user) {#user .endpoint}

```json
{
  "id": "2",
  "created_at": "2016-09-10T12:41:21Z",
  "locale": "en_US",
  "timezone": "America/Chicago",
  "type": "human",
  "username": "Wife",
  "name": "Anna",
  "content": {
    "text": "We\'re getting outta this madhouse",
    "html": "<span itemscope=\"https://pnut.io/schemas/Post\">We\'re getting outta this madhouse</span>",
    "entities": {
      "links": [],
      "mentions": [],
      "tags": []
    },
    "avatar_image": {
      "height": 1456,
      "width": 1456,
      "link": "https://d26y28lt6cxszo.cloudfront.net/avatar/rv0ORwZMYgadj74hz0eotcUuGZKKYy2O7CuplRFsrb3yo_T-TD1UYmo7j3brXq8K-VmRkv9pLRovHp1i25X7ZNO_Joo-ATXlcnIPmRehZLLyPC7LEuN5UGHetqV9qcYkHTcPzAVNgSIM",
      "is_default": false
    },
    "cover_image": {
      "height": 223,
      "is_default": true,
      "link": "https://d26y28lt6cxszo.cloudfront.net/cover/default_cover",
      "width": 960
    }
  },
  "counts": {
    "bookmarks": 1,
    "clients": 0,
    "followers": 9,
    "following": 18,
    "posts": 19,
    "users": 1
  },
  "badge": {
    "id": "1",
    "name": "Farmer"
  },
  "follows_you": false,
  "you_blocked": false,
  "you_follow": false,
  "you_muted": false,
  "you_can_follow": true
}
```

#### User Fields [<i class="fa fa-paragraph" aria-hidden="true"></i>](#user-fields) {#user-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
    </tr>

    <tr>
        <td><code>badge</code></td>
        <td>object</td>
        <td>
            Optional. Badges are earned, currently only for supporting pnut.io.
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>id</code></td>
                    <td>string</td>
                    <td>Reference ID of the badge.</td>
                </tr>

                <tr>
                    <td><code>name</code></td>
                    <td>string</td>
                    <td>Common name for the badge.</td>
                </tr>
            </table>
        </td>
    </tr>

    <tr>
        <td><code>content</code></td>
        <td>object</td>
        <td>
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>avatar_image</code></td>
                    <td>object</td>
                    <td>
                        <table>
                            <tr>
                                <th>Field</th>
                                <th>Type</th>
                                <th>Description</th>
                            </tr>

                            <tr>
                                <td><code>is_default</code></td>
                                <td>boolean</td>
                                <td>Whether or not the user's avatar is the original identicon generated for their username, or an image they uploaded.</td>
                            </tr>

                            <tr>
                                <td><code>height</code></td>
                                <td>integer</td>
                                <td>Original height of the image.</td>
                            </tr>

                            <tr>
                                <td><code>link</code></td>
                                <td>string</td>
                                <td>URL linking to the current avatar image.</td>
                            </tr>

                            <tr>
                                <td><code>width</code></td>
                                <td>integer</td>
                                <td>Original width of the image.</td>
                            </tr>
                        </table>
                    </td>
                </tr>

                <tr>
                    <td><code>cover_image</code></td>
                    <td>object</td>
                    <td>
                        <table>
                            <tr>
                                <th>Field</th>
                                <th>Type</th>
                                <th>Description</th>
                            </tr>

                            <tr>
                                <td><code>link</code></td>
                                <td>string</td>
                                <td>URL linking to the current cover image.</td>
                            </tr>

                            <tr>
                                <td><code>is_default</code></td>
                                <td>boolean</td>
                                <td>Whether or not the user has uploaded an image for their cover image, or if it is the default plain white background.</td>
                            </tr>

                            <tr>
                                <td><code>width</code></td>
                                <td>integer</td>
                                <td>Original width of the image.</td>
                            </tr>

                            <tr>
                                <td><code>height</code></td>
                                <td>integer</td>
                                <td>Original height of the image.</td>
                            </tr>
                        </table>
                    </td>
                </tr>

                <tr>
                    <td><code>entities</code></td>
                    <td>object</td>
                    <td>Rich text information for this user. See the <a href="https://pnut.io/docs/api/implementation/entities">Entities</a> documentation.</td>
                </tr>

                <tr>
                    <td><code>html</code></td>
                    <td>string</td>
                    <td>Server-generated annotated HTML rendering of user text.</td>
                </tr>
                
                <tr>
                    <td><code>markdown_text</code></td>
                    <td>string</td>
                    <td><code>text</code>, with the original markdown links preserved. Only included when looking up the authenticated user's profile.</td>
                </tr>

                <tr>
                    <td><code>text</code></td>
                    <td>string</td>
                    <td>User supplied text of the user. All Unicode characters allowed. Maximum length 256 characters. The maximum length can be retrieved from the Configuration endpoint.</td>
                </tr>
            </table>
        </td>
    </tr>

    <tr>
        <td><code>counts</code></td>
        <td>object</td>
        <td>
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>bookmarks</code></td>
                    <td>integer</td>
                    <td>Number of bookmarks this user has saved.</td>
                </tr>

                <tr>
                    <td><code>clients</code></td>
                    <td>integer</td>
                    <td>Number of public clients this user has created.</td>
                </tr>

                <tr>
                    <td><code>followers</code></td>
                    <td>integer</td>
                    <td>Number of users following this user.</td>
                </tr>

                <tr>
                    <td><code>following</code></td>
                    <td>integer</td>
                    <td>Number of users this user is following.</td>
                </tr>

                <tr>
                    <td><code>posts</code></td>
                    <td>integer</td>
                    <td>Number of posts created by this user.</td>
                </tr>

                <tr>
                    <td><code>users</code></td>
                    <td>integer</td>
                    <td>Number of users this user has brought to the network.</td>
                </tr>
            </table>
        </td>
    </tr>

    <tr>
        <td><code>created_at</code></td>
        <td>string</td>
        <td>The time at which the User was created in ISO 8601 format.</td>
    </tr>

    <tr>
        <td><code>follows_you</code></td>
        <td>boolean</td>
        <td>Whether or not this user follows you.</td>
    </tr>

    <tr>
        <td><code>id</code></td>
        <td>string</td>
        <td>Primary identifier for a user. This will be an integer, but it is always expressed as a string to avoid limitations with the way JavaScript integers are expressed. This id space is unique to User objects. There can be a Post and User with the same ID; no relation is implied.</td>
    </tr>

    <tr>
        <td><code>locale</code></td>
        <td>string</td>
        <td>User locale in ISO format.</td>
    </tr>

    <tr>
        <td><code>name</code></td>
        <td>string</td>
        <td>Optional user-supplied name. All Unicode characters allowed. Maximum length 50 characters. <em>Be sure to escape if necessary.</em></td>
    </tr>

    <tr>
        <td><code>timezone</code></td>
        <td>string</td>
        <td>User timezone in tzinfo format.</td>
    </tr>

    <tr>
        <td><code>type</code></td>
        <td>string</td>
        <td>human, feed, or bot. See <a href="https://pnut.io/docs/resources/account-types">Account Types</a> to be sure of the implications.</td>
    </tr>

    <tr>
        <td><code>username</code></td>
        <td>string</td>
        <td>Case sensitive. 20 characters, may only contain a-z, 0-9 and underscore.</td>
    </tr>

    <tr>
        <td><code>you_blocked</code></td>
        <td>boolean</td>
        <td>Whether or not you blocked this user.</td>
    </tr>

    <tr>
        <td><code>you_can_follow</code></td>
        <td>boolean</td>
        <td>Whether or not you <em>can</em> follow this user -- not taking into account <code>you_follow</code>.</td>
    </tr>

    <tr>
        <td><code>you_follow</code></td>
        <td>boolean</td>
        <td>Whether or not you follow this user.</td>
    </tr>

    <tr>
        <td><code>you_muted</code></td>
        <td>boolean</td>
        <td>Whether or not you muted this user.</td>
    </tr>

    <tr>
        <td><code>verified</code></td>
        <td>object</td>
        <td>
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>domain</code></td>
                    <td>string</td>
                    <td>Optional domain verified to be owned by the user</td>
                </tr>

                <tr>
                    <td><code>link</code></td>
                    <td>string</td>
                    <td>Optional URL verified to be owned by the user</td>
                </tr>
            </table>
        </td>
    </tr>
</table>



#### General User Parameters [<i class="fa fa-paragraph" aria-hidden="true"></i>](#general-user-parameters) {#general-user-parameters}

Any endpoint that returns user objects (including any that return post objects, message objects, etc.) can be subject to these parameters.

##### General Parameters

Name|Type|Description
-|-|-
`include_html`|integer (0 or 1)|Should the post and user `html` field be included alongside the `text` field in the response objects? Defaults to true.
`include_user_html`|integer (0 or 1)|Should the user `html` field be included alongside the `text` field in the response objects? Defaults to true. Note that `include_html` takes priority if present.
`include_counts`|integer (0 or 1)|Include the user's counts. Defaults to true.
`include_user`|integer (0 or 1)|Return the user as their complete object, or only as (string) ID if false. Defaults to true.
`include_presence`|integer (0 or 1)|Include the user's current presence. Defaults to false.
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects. Defaults to false.
`include_user_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all user objects. Defaults to false.
