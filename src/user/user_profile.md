# User Profile 

## `UserProfile`

```rust
pub struct UserProfile {
    pub user_id: i32,
    pub name: Option<String>,
    pub description: Option<String>,
    pub display_name: Option<String>,
    pub pfp: Option<String>,
    pub banner: Option<String>,
}
```

> User profile defaults have not been discussed.

## `UserProfilePartial`

```rust
pub struct UserProfilePartial {
    pub name: Option<String>,
    pub description: Option<String>,
    pub display_name: Option<String>,
    pub pfp: Option<String>,
    pub banner: Option<String>,
}
```

This type is used when modifying user data.
If a provided field is null, the data will not be modified.
