## [THash](../thash.md).GetDigest

Outputs message digest

---
### Syntax
```delphi
procedure THash.GetDigest(out Buffer; BufSize: Cardinal);
```
### Parameters
*   *Buffer*: output buffer for message digest
*   *BufSize*: size of output buffer (in bytes)

### Remarks
*   if *BufSize* differs from the message digest size, exception is raised

### See also
*   [Digest](digest.md), [DigestSize](digestsize.md)

### Examples
```delphi
var
  SHA256: THash;
  Digest: TSHA256Digest;

begin
  SHA256:= THash.SHA256;
  SHA256.Update(Data, DataSize);
  SHA256.GetDigest(Digest, SizeOf(Digest));
  ...
end;
```
