#Import friends

```shell
curl https://demo.buddycloud.org/api/???? \
 --??? \
 --???
```

```javascript```
???
???
```

```json
???
???
```

You can improve your users' onboarding experience by comparing existing social graphs (for example from Facebook or email address books) to match for friends already using Buddycloud.

The results of this query are usually displayed to the end user as a "People you may know" screen.

As the friend finder is agnostic to the social graph that holds the user's identification handle, one can use arbitary identification providers. Examples of providers that are currently in use are:

* email address
* phone number (last 6 digits)
* Twitter (handle without the starting '@')
* Facebook (numeric id, as returned in https://developers.facebook.com/tools/explorer/145634995501895/?method=GET&path=me%3Ffields%3Did%2Cname&version=v2.0)

###Privacy
The [friend finder](http://github.com/buddycloud/friend-finder) service matains the user's privacy by only ever uploading hashes of identifiers - never the users or their address friends' real email, phone number or other private information.

You should also request your users permission before uploading any identifiers.

To create a hash:

1. Append the provider and the identifier, separated by a colon. E.g. ```facebook:1015747641```

2. Apply a sha256 hash function to the string

A POST to this endpoint will publish user contacts' hashes and match previously reported hashes to jids. 

### HTTP Request
`POST https://demo.buddycloud.org/api/match_contacts`

##Social Graph comparison

```shell
curl -H "Content-Type: application/json" -d '{"mine": ["0a22c6c85a47116509f8fbb7688c98ac480651db3c54dd3fcd2ce34d48a5025b"], "others": ["023476e7b8be135f970d65f9bee53bfc66c43742815cdcd2c7f53e51f3937b17", "bcee94d395fe9cd76dfae390e006a98032144fb48dc8181448c4cd192ec4b75c"]}' https://demo.buddycloud.org/api/match_contacts \
 --200 OK \
 --{
    "items": [
        {
            "jid": "alice@example.com",
            "matched-hash": "023476e7b8be135f970d65f9bee53bfc66c43742815cdcd2c7f53e51f3937b17"
        }
    ]
   }
```

```javascript```
???
???
```

```json
???
???
```

@Abmar: please complete.

### HTTP Request
`POST https://demo.buddycloud.org/api/????`