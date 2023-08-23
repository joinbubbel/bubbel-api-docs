# Response Types

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
