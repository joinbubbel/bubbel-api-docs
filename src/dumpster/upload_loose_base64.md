# `upload_loose_base64`

Last Update Commit: `da83974`

Function name: `bubbelApiLooseBase64`

## Request

```rust
pub struct InUploadLooseBase64 {
    #[flatten]
    req: UploadLooseBase64,
}

pub struct UploadLooseBase64 {
    pub token: UserToken,
    pub file_name: String,
    pub data: String,
}
```

Upload a base64 string using the file name `file_name`.
This file is "loose" meaning that it doesn't belong to any class.
This is ideal for file attachments which can be of any type.

## Response

```rust
pub ResUploadLooseBase64 {
    res: Option<UploadLooseBase64Out>,
    error: Option<UploadLooseBase64Error>
}

pub struct UploadLooseBase64Out {
    pub object_name: String,
}
```

## Error

```rust
pub enum UploadLooseBase64Error {
    NoAuth,
    InvalidBase64,
    DataConstraint { data_constraint_error: String },
    Internal { ierror: String },
}
```

`NoAuth` means that `token` is invalid.

`InvalidBase64` is thrown if `data` contains an invalid base64 string.

`DataConstraint` indicates that some constraints (like max file size for example) are preventing the file from being uploaded.

## Notes

None

