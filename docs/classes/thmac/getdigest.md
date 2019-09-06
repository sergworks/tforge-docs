## [THMAC](../thmac.md).GetDigest

Outputs message authentication code

---
### Syntax
```delphi
procedure THMAC.GetDigest(out Buffer; BufSize: Cardinal);
```
### Parameters
*   *Buffer*: output buffer for message digest
*   *BufSize*: size of output buffer (in bytes)

### Remarks
*   if *BufSize* differs from the message digest size, exception is raised

### See also
*   [Digest](digest.md), [DigestSize](digestsize.md)

