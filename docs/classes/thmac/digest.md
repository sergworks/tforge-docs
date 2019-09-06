## [THMAC](../thmac.md).Digest

Computes and returns final message authentication code

---
### Syntax
```delphi
function THMAC.Digest: ByteArray;
```
### See also

*   [DigestSize](digestsize.md), [GetDigest](getdigest.md)

### Examples
*   Compute _HMAC-SHA1_ message authentication code for a file:

```delphi
procedure SHA1FileMAC(const Key: ByteArray; const FileName: string);
begin
  Writeln('HMAC: ', THMAC.SHA1.Init(Key).UpdateFile(FileName).Digest.ToHex);
end;
```
