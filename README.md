# ceuazul

Blue Sky API Client

## How to obtain a Session Token

```
% export BLUESKY_HANDLE="username.bsky.social"
% export BLUESKY_APP_PASSWORD="idgaf-wtf-5boob-abcd"
% curl -s -H "Content-Type: application/json" -X POST "https://bsky.social/xrpc/com.atproto.server.createSession" -d "{ \"identifier\":\"$BLUESKY_HANDLE\", \"password\":\"$BLUESKY_APP_PASSWORD\" }"
```

