# `/api/auth_user`

Last Update Commit: `8c0ef88`

Function name: `bubbelApiAuthUser`

## Request

```rust
pub struct InAuthUser {
    #[flatten]
    req: AuthUser,
}

pub struct AuthUser {
    pub username: String,
    pub password: String,
}
```

## Response

```rust
pub struct ResAuthUser {
    res: Option<AuthUserOut>,
    error: Option<AuthUserError>,
}

pub struct AuthUserOut {
    pub token: UserToken,
    pub username: String,
    pub email: String,
}
```

The returned `token` is now used to identify the user's login session.

## Error

```rust
pub enum AuthUserError {
    InvalidCredentials,
    InvalidPasswordCryto,
    UserNotFound,
    UserNotVerified {
        user_id: UserId,
    },
    Internal {
        ierror: String,
    },
}
```

`InvalidPasswordCryto` should never occur.

## Notes

A user cannot log in until their account is email verified.

