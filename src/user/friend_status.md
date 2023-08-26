# Friend Status

For a friend connection to be fully formed, both users must add each other.
Let's make up two users A and B.

```rust
//  VERY IMPORTANT:
//  Special enum case here!
//  Read to the end!
pub enum FriendStatus {
    SentPending,
    RecievedPending,
    Full,
}
```

If A adds B, A is `SentPending`.
In other words, A has sent a connection and is now waiting for a reply.
B is `RecievedPending`.
In simple terms, B has recieved a connection.
When B adds A back, they have now formed a `Full` connection.

## The special `enum` case.

> This is VERY IMPORTANT information.

The `FriendStatus` enum is equivalent to a string.

Rather than being like this:

```json
{
    "type": "Full",
}
```

`FriendStatus` is just a string. There is no `type` field.

```
"Full"
```

