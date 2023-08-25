# Response Types

`DataChannelResponse`s are regularly received after initialization.
This page describes all possible responses and response types.

> Note that ANY INCORRECT USE OF TYPES will most likely result in the socket closing without an error.

## `DataChannelResponse`

```rust
pub struct DataChannelResponse {
    pub res: Option<DataChannelResponseType>,
    pub error: Option<DataChannelError>,
}
```

## `DataChannelResponseType`

```rust
pub enum DataChannelResponseType {
    OnNew(DataChannelOnNew),
}
```

All response possibilities are listed below.

## `DataChannelError`

```rust
pub enum DataChannelError {
    NoAuth,
    ChannelNotFound,
    Internal { ierror: String },
}
```

`NoAuth` can occur if the user has been logged out.
`ChannelNotFound` can occur if the channel has been deleted.

## On New Data: `OnNew`

`OnNew` occurs when a new data has been sent into the channel.

```rust
pub struct DataChannelOnNew {
    pub item: DataChannelItem,
}
```

`DataChannelItem` is described [here](./messages/message.md).

