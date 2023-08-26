# `/api/deauth_user`

Last Update Commit: `8c0ef88`

Function name: `bubbelApiDeauthUser`

## Request

```rust
pub struct InDeauthUser {
    #[flatten]
    req: DeauthUser,
}

pub struct DeauthUser {
    pub token: UserToken,
}
```

This request will invalidate `token`, essentially logging the user out.

## Response

```rust
type ResDeauthUser = Null;
```

`ResDeauthUser` returns nothing no matter what.

## Notes

None

