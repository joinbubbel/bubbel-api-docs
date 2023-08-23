# Request Types

## `DataChannelRequest`

```rust
pub struct DataChannelRequest {
    pub token: UserToken,
    pub command: DataChannelCommandType,
}
```

## `DataChannelCommandType`

```rust
pub enum DataChannelCommandType {
    Send(DataChannelCommandSend),
    Delete(DataChannelCommandDelete),
}
```

## `DataChannelCommandType`

```rust
pub enum DataChannelCommandType {
    Send(DataChannelCommandSend),
    Delete(DataChannelCommandDelete),
}
```

