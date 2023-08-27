# API Route

Last Update Commit: `2e4458d`

Function name: `bubbelApiGetDataChannelChunk`

## Request

```rust
pub struct InGetDataChannelChunk {
    #[flatten]
    req: GetDataChannelChunk,
}

pub struct GetDataChannelChunk {
    token: UserToken,
    channel_id: DataChannelId,
    chunk_index: DataChunkIndex,
}
```

`chunk_index` starts at zero and counts up.

## Response

```rust
pub struct ResGetDataChannelChunk {
    res: Option<GetDataChannelChunkOut>,
    error: Option<GetDataChannelChunkError>,
}

pub struct GetDataChannelChunkOut {
    chunk: DataChunk,
}

pub struct DataChunk {
    items: Vec<Option<DataChannelItem>>,
}
```

The field `items` may contain null items, representing deleted messages.
`DataChannelItem` can be found [here](./messages/message.md).

## Error

```rust
pub enum GetDataChannelChunkError {
    NoAuth,
    ChunkNotFound,
    ChannelNotFound,
    Internal { ierror: String },
}
```

`NoAuth` means that `token` is invalid or that you are not authorized to read the channel.

`ChunkNotFound` occurs if `chunk_index` is invalid.

`ChannelNotFound` occurs if `channel_id` is invalid.

## Notes

