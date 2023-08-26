# `/api/remove_friend`

Last Update Commit: `8c0ef88`

Function name: `bubbelApiRemoveFriend`

## Request

```rust
pub struct InRemoveFriend {
    #[flatten]
    req: RemoveFriend,
}

pub struct RemoveFriend {
    pub token: UserToken,
    pub removal_id: UserId,
}
```

`removal_id` represents the person you want to purge from your life.
Note that this function can also be used to "decline" a friend connection.

## Response

```rust
pub struct ResRemoveFriend {
    error: Option<RemoveFriendError>
}
```

This method has no response data.

## Error

```rust
pub enum RemoveFriendError {
    NoAuth,
    Internal { ierror: String },
}
```

`NoAuth` is thrown if the `token` is invalid.

## Notes

None

