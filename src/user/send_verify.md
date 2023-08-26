# `/api/send_verify`

Last Update Commit: `8c0ef88`

Function name: `bubbelApiSendVerify`

## Request

```rust
pub struct SendVerify {
    pub user_id: UserId,
}
```

## Response

```rust
struct ResSendVerify {
    error: Option<SendVerifyError>
}
```

This method has no response data.

## Error

```rust
pub enum SendVerifyError {
    UserNotFound,
    ResendTooSoon,
    SendVerification,
    Internal {
        ierror: String,
    },
}
```

`ResendTooSoon` is thrown when an email was too recently sent out.

`SendVerification` is thrown when the verification email could not be sent.

> Resend times have not been properly discussed yet.

## Notes

None

