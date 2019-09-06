## [THash](../thash.md).DoneInstance

Outputs message digest

---
### Syntax
```delphi
procedure THash.DoneInstance(out Digest);
```
### Parameters
*   *Digest*: final message digest

### Remarks
*   *DoneInstance* method does not check the size of output buffer;
*   *THash.InitInstance*, *THash.UpdateInstance* and *THash.DoneInstance* methods constitute traditional (non-fluent) hash-computing API.

### See also
*   [Digest](digest.md), [GetDigest](getdigest.md)

### Examples
```delphi
var
  SHA256: THash;
  Digest: TSHA256Digest;

begin
  SHA256:= THash.SHA256;
  SHA256.Update(Data, DataSize);
  SHA256.DoneInstance(Digest);
  ...
end;
```
