# Request Types

`DataChannelRequest` represents all possible commands that may be sent to the server.

> Note that ANY INCORRECT USE OF TYPES will most likely result in the socket closing without an error.

## `DataChannelRequest`

```rust
pub struct DataChannelRequest {
    pub token: UserToken,
    pub command: DataChannelCommandType,
}
```

An invalid `token` will cause an error to be sent back.

## `DataChannelCommandType`

```rust
pub enum DataChannelCommandType {
    Send(DataChannelCommandSend),
    Delete(DataChannelCommandDelete),
    Edit(DataChannelCommandEdit),
}
```

## Sending Data: `Send`

```rust
pub struct DataChannelCommandSend {
    message: Message,
}
```

All `Message` types can be found [here](./messages/message.md).

Only the `NoAuth` and `ChannelNotFound` errors may occur.

## Deleting Data: `Delete`

```rust
pub struct DataChannelCommandDelete {
    chunk: DataChunkIndex,
    index: Integer,
}
```

All `Message` types can be found [here](./messages/message.md).
`chunk` refers to the index of the data chunk containing the message and `index` refers to the message's index within the chunk.

The errors `NoAuth`, `ChunkNotFound`, `DataItemNotFound`, and `DataItemDeleted` may occur.

## Editing Data: `Edit`

```rust
pub struct DataChannelCommandEdit {
    chunk: DataChunkIndex,
    index: Integer,
    new_message: Message,
}
```

All `Message` types can be found [here](./messages/message.md).
`chunk` refers to the index of the data chunk containing the message and `index` refers to the message's index within the chunk.

The errors `NoAuth`, `ChunkNotFound`, `DataItemNotFound`, and `DataItemDeleted` may occur.

