# `/api/get_user_profile`

Last Update Commit: `8c0ef88`

Function name: `bubbelApiGetUserProfile`

## Request

```rust
pub struct GetUserProfile {
    pub user_id: UserId,
    pub token: Option<UserToken>,
}
```

`token` is optional but should be provided for signed in users as some profiles may be private.

## Response

```rust
pub struct GetUserProfileOut {
    #[flatten]
    pub profile: UserProfile,
}
```

## Error

```rust
pub enum GetUserProfileError {
    NoAuth,
    UserNotFound,
    Internal { ierror: String },
}
```

`NoAuth` is thrown when either `token` is invalid or the user is not authorized to view the profile.

## Notes

See [`UserProfile`](./user_profile.md).

