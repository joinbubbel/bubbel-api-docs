# `/api/verify_account`

Last Update Commit: `8c0ef88`

Function name: `bubbelApiVerifyAccount`

## Request

```rust
pub struct VerifyAccount {
    pub code: String,
}
```

## Response

```rust
pub struct ResVerifyAccount {
    error: Option<VerifyAccountError>
}
```

This method does not have any response data.

## Error

```rust
pub enum VerifyAccountError {
    CodeTimedOutOrAlreadyVerifiedOrInvalidCode,
    Internal {
        ierror: String,
    },
}
```

`CodeTimedOutOrAlreadyVerifiedOrInvalidCode` is my favorite error message of all time as well as the least helpful error on this planet.

## Notes

> Account verification code expiration times have not been discussed.

