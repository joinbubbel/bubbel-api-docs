# `/api/set_user_profile`

Last Update Commit: `da83974`

Function name: `bubbelApiSetUserProfile`

## Request

```rust
pub struct InSetUserProfile {
    #[flatten]
    req: SetUserProfile,
}

pub struct SetUserProfile {
    pub token: UserToken,
    #[serde(flatten)]
    pub profile: UserProfilePartial,
}
```

See [`UserProfilePartial`](./user_profile.md).

## Response

```rust
type ResSetUserProfile {
    error: Option<SetUserProfile>,
}
```

## Error

```rust
pub enum SetUserProfileError {
    NoAuth,
    Internal { ierror: String },
}
```

`NoAuth` means that `token` is invalid.

## Notes

See [`UserProfilePartial`](./user_profile.md).

