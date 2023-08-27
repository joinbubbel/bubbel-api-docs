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
    OnDelete(DataChannelOnDelete),
    OnEdit(DataChannelOnEdit),
}
```

All response possibilities are listed below.

## `DataChannelError`

```rust
pub enum DataChannelError {
    NoAuth,
    ChannelNotFound,
    ChunkNotFound,
    DataItemNotFound,
    DataItemDeleted,
    Internal { ierror: String },
}
```

`NoAuth` can occur if the user has been logged out.

`ChannelNotFound` can occur if the channel has been deleted.

`ChunkNotFound` can occur for commands that include a chunk index if the index is invalid.

`DataItemNotFound` can occur for for commands that include a data item index if the index is invalid.

`DataItemDeleted` occurs when trying to access an item that has already been deleted.

## On New Data: `OnNew`

`OnNew` occurs when a new data has been sent into the channel.

```rust
pub struct DataChannelOnNew {
    pub item: DataChannelItem,
    pub chunk: DataChunkIndex,
    pub index: Integer,

}
```

`DataChannelItem` is described [here](./messages/message.md).

`chunk` and `index` are used to identify this specific message when editing or deleting the message.

## On Data Deleted: `OnDelete`

```rust
pub struct DataChannelOnDelete {
    pub chunk: DataChunkIndex,
    pub index: Integer,
}
```

`chunk` and `index` are used to identify the message that has been deleted.

## On Data Edited: `OnEdit`

```rust
pub struct DataChannelOnEdit {
    pub chunk: DataChunkIndex,
    pub index: Integer,
    pub new_item: DataChannelItem,
}
```

`chunk` and `index` are used to identify the message that has been edited, and `new_item` contains the new message item.
`DataChannelItem` is described [here](./messages/message.md).

