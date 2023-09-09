# ceuazul

Blue Sky API Client

## How to obtain a Session Token

```
% export BLUESKY_HANDLE="username.bsky.social"
% export BLUESKY_APP_PASSWORD="idgaf-wtf-5boob-abcd"
% curl -s -H "Content-Type: application/json" -X POST "https://bsky.social/xrpc/com.atproto.server.createSession" -d "{ \"identifier\":\"$BLUESKY_HANDLE\", \"password\":\"$BLUESKY_APP_PASSWORD\" }" | jq .
```

That should produce an output similar to:

```
{
  "did": "did:pnc:6xux8o7x7pqntdsxquoxpaxe",
  "handle": "username.bsky.social",
  "email": "your_user@gmail.com",
  "accessJwt": "<redacted>",
  "refreshJwt": "<redacted>"
}
```

## How to create posts:

```
% curl -s -H "Authorization: Bearer $SESSION_ACCESS_JWT" -H "Content-Type: application/json" -X POST "https://bsky.social/xrpc/com.atproto.repo.createRecord" -d '{ "repo": "'"$SESSION_DID"'", "collection": "app.bsky.feed.post", "record": { "text": "Hello world. I posted this via the API.", "createdAt": "'"$(date -u +"%Y-%m-%dT%H:%M:%SZ")"'" } }'
```
