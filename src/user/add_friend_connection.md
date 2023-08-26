# `/api/add_friend_connection`

Last Update Commit: `8c0ef88`

Function name: `bubbelApiAddFriendConnection`

## Request

```rust
pub struct InAddFriendConnection {
    #[flatten]
    req: AddFriendConnection,
}

pub struct AddFriendConnection {
    pub token: UserToken,
    pub receiver_id: UserId,
}
```

See the [`FriendStatus`](./friend_status.md)
page for details on how friend connections work.

## Response

```rust
pub struct ResAddFriendConnection {
    error: Option<AddFriendConnectionError>,
}
```

This method has no response data.

## Error

```rust
pub enum AddFriendConnectionError {
    NoAuth,
    CannotAddSelf,
    AlreadyConnected,
    Internal { ierror: String },
}
```

`NoAuth` means that `token` is invalid.

`CannotAddSelf` occurs when you try to friend yourself (that's just sad man).

`AlreadyConnected` means that you've already connected with this user.

## Notes

None

