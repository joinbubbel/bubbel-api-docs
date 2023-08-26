# User API Identifier Types

## `UserId`

```rust
pub struct UserId(Integer);
```

`UserId`s are simply just 32-bit numbers;

## `UserToken`

```rust
pub struct UserToken(String);
```

`UserToken`s are simply strings that represent a user's login session.
Note that tokens automatically become invalid on server restarts.

> `UserToken` expiration has not been fully discussed yet.

