# `/api/username_to_id`

Last Update Commit: f9ec683

Function name: `bubbelApiUsernameToId`

## Request

```rust
pub struct UsernameToId {
    username: String,
}
```

Converts `username` into its respective `user_id`.

## Response

```rust
pub struct UsernameToIdOut {
    user_id: UserId,
}
```

## Error

```rust
pub enum UsernameToIdError {
    UserNotFound,
    Internal { ierror: String },
}
```

## Notes

None

