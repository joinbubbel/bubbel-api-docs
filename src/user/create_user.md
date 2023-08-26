# `/api/create_user`

Last Update Commit: `8c0ef88`

Function name: `bubbelApiCreateUser`

## Request

```rust
pub struct InCreateUser {
    #[flatten]
    req: CreateUser,
}

pub struct CreateUser {
    pub email: String,
    pub username: String,
    pub password: String,
}
```

> Limits on `email`, `username`, and `password` have yet to be properly discussed.

## Response

```rust
pub struct CreateUserOut {
    pub user_id: UserId,
}
```

## Error

```rust
pub enum CreateUserError {
    InvalidEmail,
    InvalidUsername,
    InvalidPassword,
    InvalidPasswordCryto,
    EmailOrUsernameTaken,
    Internal {
        ierror: String,
    },
}
```

`EmailOrUsernameTaken` can occur if an account has been created but not been email verified.

`InvalidPasswordCryto` indicates that an error was thrown by a cryptography function.
This should never occur.

## Notes

None

