# `/api/delete_user`

Last Update Commit: `da83974`

Function name: `bubbelApiDeleteUser`

## Request

```rust
pub struct InDeleteUser {
    #[flatten]
    req: InDeleteUser,
}

pub struct DeleteUser {
    pub token: UserToken,
}

```

## Response

```rust
pub struct ResDeleteUser {
    error: Option<DeleteUserError>,
}
```

## Error

```rust
pub enum DeleteUserError {
    NoAuth,
    Internal { ierror: String },
}
```

`NoAuth` means that `token` is invalid.

## Notes

None

