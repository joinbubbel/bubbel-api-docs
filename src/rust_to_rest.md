# Rust to REST

All API bindings are generated from Rust code, so it's essential to understand how these types are converted.

When describing types in this documentation, I will use my own Rust-Typescript hybrid language.

Even if you do not know rust, I've highlighted 3 basic representations that I will use: `struct`, `enum`, and flattened `struct`.

## `struct` Representation

### Rust

```rust
struct MyType {
    name: String
    user_data: String,
    optional_data: Option<String>,
}
```

### JSON

```json
{
    "name": "Some String",
    "user_data": "Some Data",
    "optional_data": "This could be null."
}
```

### Typescript

> The typescript representation is by far the most straight forward.

```typescript
interface MyType {
    name: String
    user_data: String
    optional_data: String | null
}
```

### Swift

> In certain programming languages, like swift, camel case is enforced.

```swift
struct MyType: Codable {
    let name: String
    let userData: String
    let optionalData: String?

    enum CodingKeys: String, CodingKey {
        case userData = "user_data"
        case optionalData = "optional_data"
    }
}
```

## `enum` Representation

```rust
struct MyType {
    name: String
    user_data: String,
    optional_data: Option<String>,
}

enum MyEnum {
    Unicorn,
    Pony {
        pony_name: String,
    },
    OtherType(MyType),
}
```

### JSON (Possibilities)

```json
{
    "type": "Unicorn",
}
```

```json
{
    "type": "Pony",
    "pony_name": "Jaquavious"
}
```

```json
{
    "type": "OtherType",
    "name": "Some String",
    "user_data": "Some Data",
    "optional_data": "This could be null."
}
```

### Typescript

```typescript
interface MyEnum {
    type: "Unicorn" | "Pony" | "OtherType",

    pony_name: String | null,

    name: String | null,
    user_data: String | null,
    optional_data: String | null,
}
```

> There are a few execptions in these docs, but I will point them out.

## Flattened `struct` Representation

### Rust

```rust
struct FooType {
    hello: String,
    world: String,
}

struct BarType {
    bubbel: String,

    #[flatten]
    some_inner_data: FooType,
}
```

### JSON

```json
{
    "bubbel": "...",

    "hello": "...",
    "world": "...",
}
```

> Note how the `some_inner_data` no longer appears.
> It has been flattened.

### Typescript

```typescript
interface BarType {
    bubbel: String,

    hello: String,
    world: String,
}
```

