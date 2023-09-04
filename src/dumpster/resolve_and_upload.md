# `/api/resolve_and_upload`

Last Update Commit: `da83974`

Function name: `bubbelApiResolveAndUpload`

## Request

```rust
pub struct InResolveAndUpload {
    #[flatten]
    req: ResolveAndUpload,
}

pub struct ResolveAndUpload {
    token: UserToken,
    url: String,
}
```

Make a GET request to `url`, loosely storing the result using [`/api/upload_loose_base64`](./upload_loose_base64.md).

## Response

```rust
pub struct ResResolveAndUpload {
    res: Option<ResolveAndUploadOut>,
    error: Option<ResolveAndUploadError>,
}

pub struct ResolveAndUploadOut {
    object_name: String,
}
```

## Error

```rust
pub enum ResolveAndUploadError {
    FetchFailed { fetch_error: String },
    FetchBytesFailed { fetch_bytes_error: String },
    CannotGetUrlFileName,
    ConvertToBase64Failed,
    NoAuth,
    DataConstraint { data_constraint_error: String },
    Internal { ierror: String },
}
```

`NoAuth` means that `token` is invalid.

`FetchFailed` occurs if the GET request to `url` fails.

`FetchBytesFailed` occrs if we fail to load the bytes of the response.

`CannotGetUrlFileName` if we fail to extract the file name portion of the request url.
For example, in "https://example.com/abc.png", `abc.png` is the file name.

See [`UploadLooseBase64Error`](./upload_loose_base64.md).

## Notes

None

