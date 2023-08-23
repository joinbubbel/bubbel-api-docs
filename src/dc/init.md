# `Initialization`

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
    /// `null` if there was an `error`
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

