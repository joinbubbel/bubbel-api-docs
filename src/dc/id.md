# Identifier Types

Data Channels and Data chunks are both refered to with numbers.

## `DataChannelId`

```rust
pub type DataChannelId = Integer;
```

## `DataChunkIndex`

```rust
pub type DataChunkIndex = Integer;
```

The following assumption is respected: indices start at 0 and count up.

