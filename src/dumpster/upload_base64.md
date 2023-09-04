# `/api/upload_base64`

Last Update Commit: `da83974`

Function name: `bubbelApiUploadBase64`

## Request

```rust
pub struct InUploadBase64 {
    #[flatten]
    req: UploadBase64,
}

pub struct UploadBase64 {
    token: UserToken,
    class_name: String,
    data: String,
}
```

Upload a base64 string to a specific class.
See the [classes](./classes.md)
here.

## Response

```rust
pub struct ResUploadBase64 {
    res: Option<UploadBase64Out>,
    error: Option<UploadBase64Error>,
}

pub struct UploadBase64Out {
    object_name: String,
}
```

## Error

```rust
pub enum UploadBase64Error {
    NoAuth,
    InvalidBase64,
    DataCorrupt { data_corrupt_error: String },
    DataConstraint { data_constraint_error: String },
    Internal { ierror: String },
}
```

`NoAuth` means that `token` is invalid.

`InvalidBase64` is thrown if `data` contains an invalid base64 string.

`DataCorrupt` indicates that the wrong file type was sent, or the file type isn't recognized.

`DataConstraint` indicates that some constraints (like max file size for example) are preventing the file from being uploaded.

## Notes

None

