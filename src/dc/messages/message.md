# Message Types

## `DataChannelItem`

```rust
pub struct DataChannelItem {
    sender: UserId,
    post_time: UnixTime,
    edit_time: Option<UnixTime>,
    message: Message,
}
```

Contains a `message` as well as additional metadata about the message.

## `Message`

```rust
pub enum Message {
    Text(Text),
}
```

Lists each type of message that can be passed through a channel.

