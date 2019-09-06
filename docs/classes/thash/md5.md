## [THash](../thash.md).MD5

Creates *THash* instance implementing *MD5* algorithm

---
### Syntax
```delphi
class function THash.MD5: THash;
```
### Remarks

*   *MD5* is **not** collision-resistant
*   *MD5* is Merkle–Damgård hash function
*   *MD5* digest size is 16 bytes (128 bits)

### Examples

*   compute *MD5* digest of a file:
```delphi
procedure CalcMD5(const FileName: string);
begin
  Writeln('MD5:  ', THash.MD5.UpdateFile(FileName).Digest.ToHex);
end;
```
