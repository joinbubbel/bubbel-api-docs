# Flow

The flow of the data channel is as follows:

```
client === server

# First, initialize the data channel.

DataChannelInitRequest  =send>
DataChannelInitResponse <recv=

# Now, recieve messages from the websocket.

DataChannelResponse     <recv=

# You can also, send messages from the websocket.

DataChannelRequest      =send>
```

Also remember to load saved chunks.
You can do this using the following typescript:

```typescript
let initResponse = initMessage as backend.DataChannelInitResponse;
for (let i = initResponse.current_chunk!; i >= 0; i--) {
    let loadedChunk = await bubbelApiGetDataChannelChunk({
        channel_id: channelId,
        chunk_index: 0,
        token,
    });
    if (loadedChunk.error) {
        //  Got error.
    } else {
        for (let itemIndex in loadedChunk.res!.chunk.items) {
            let item = loadedChunk.res!.chunk.items[itemIndex];
            //  Got chunk item.
        }
    }
}

```

