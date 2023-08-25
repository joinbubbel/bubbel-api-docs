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
}
```

## Sending Data: `Send`

```rust
pub struct DataChannelCommandSend {
    message: Message,
}
```

All `Message` types can be found [here](./messages/message.md).

## Deleting Data: `Delete`

> Work in Progress!

