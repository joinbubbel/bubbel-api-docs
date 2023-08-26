# `/api/check_token`

Last Update Commit: `8c0ef88`

Function name: `bubbelApiCheckToken`

## Request

```rust
pub struct CheckToken {
    token: UserToken,
}
```

This request check if `token` is valid, or in other words, if the user is logged in.

## Response

```rust
pub struct ResCheckToken {
    res: Option<CheckTokenOut>,
}

pub struct CheckTokenOut {
    user_id: Option<UserId>,
}
```

`res` is never null.

If the token is valid, `user_id` is the id of the logged in user.

## Error

```rust
pub enum CheckTokenError {
    Ignore,
}
```

This method cannot throw errors, so this value should be ignored.

## Notes

None

