# `Initialization`

To initialize the data channel, first send a `DataChannelInitRequest`.
If all goes well, `DataChannelInitResponse` is sent back.

If ANY OTHER DATA is sent at this point, the socket simply closes.
If either `token` or `channel` are invalid, `error` will be set.

If there are no errors, `current_chunk` will be set.

## `DataChannelInitRequest`

```rust
pub struct DataChannelInitRequest {
    pub token: UserToken,
    pub channel: DataChannelId,
}
```

## `DataChannelInitResponse`

```rust
pub struct DataChannelInitResponse {
    pub current_chunk: Option<DataChunkIndex>,
    pub error: Option<DataChannelInitError>,
}
```

## `DataChannelInitError`

```rust
pub enum DataChannelInitError {
    NoAuth,
    ChannelNotFound,
    Internal { ierror: String },
}
```

`NoAuth` occurs when `token` is invalid.
`ChannelNotFound` can occur either if the channel doesn't exist or if it has been deleted.

