# REST APIs

My code philosophy revolves around simplicity and consistency for understanding.
In other words, when I write code, I want it to be easy to understand, and I accomplish this by making code consistency.

These decisions are reflected through Bubbel's REST API.
All types follow the EXACT SAME FORMAT, so pay attention!

## Requests

Requests always look like this:

```rust
struct InFoo {
    #[flatten]
    req: Foo
}

struct Foo {
    some_field: String,
    other_field: String,
}
```

> Note that `req` is flattened and therefore doesn't actually appear in any requests.

## Responses

Responses always look like this:

```rust
struct ResFoo {
    res: Option<FooOut>,
    error: Option<FooError>,
}

struct FooOut {
    some_output: String,
}
```

Here, responses can either `error` is null and `res` is set, or the inverse.
For some APIs, `res` is simply always null.

## Errors

```rust
struct FooError {
    SomeError,
    Internal {
        ierror: String,
    }
}
```

Pretty much all error types will have an `Internal` error.
This is an error that should NEVER occur.
If you do happen to get this, it should be reported.

## Other Errors

When fetching, two other errors may occur.

1. A response of `Failed to Serialize XXX` indicates that you used your types incorrectly!
Be sure to triple check the docs!
2. Other errors generally occur either if the user isn't connected to the internet or the server is down.

