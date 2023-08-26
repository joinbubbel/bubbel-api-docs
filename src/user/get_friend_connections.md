# `/api/get_friend_conenctions`

Last Update Commit: `8c0ef88`

Function name: `bubbelApiGetFriendConnections`

## Request

```rust
pub struct GetFriendConnections {
    pub token: UserToken,
}
```

## Response

```rust
pub struct GetFriendConnectionsOut {
    pub friend_connections: HashMap<UserId, FriendStatus>,
}
```

## Error

```rust
pub enum GetFriendConnectionsError {
    NoAuth,
    Internal { ierror: String },
}
```

`NoAuth` is thrown if `token` is invalid.

## Notes

See [`FriendStatus`](./friend_status.md).

