## [THash](../thash.md).Digest

Computes and returns final message digest

---
### Syntax
```delphi
function THash.Digest: ByteArray;
```
### See also

*   [DigestSize](digestsize.md), [GetDigest](getdigest.md)

### Examples
```delphi
procedure SHA256FileDigest(const FileName: string);
begin
  Writeln('SHA256: ', THash.SHA256.UpdateFile(FileName).Digest.ToHex);
end;
```
