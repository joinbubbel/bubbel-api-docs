# Flow

## Websocket Flow

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

Essentially, you will need to send an `DataChannelInitRequest` to start the data channel.
Sending ANY OTHER DATA will cause the channel to close.
A `DataChannelInitResponse` will be recieved containing the chunks that need to be loaded.
All messages afterwards are `DataChannelResponse`s.
Commands can be sent with `DataChannelRequest`.

> Note that ANY INCORRECT USE OF TYPES will most likely result in the socket closing without an error.

## Chunk Loading

You can load data chunks with the following typescript.

```typescript
let initResponse = initMessage as backend.DataChannelInitResponse;
if (initResponse.error) {
    //  Got Error.
} else {
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
}
```

