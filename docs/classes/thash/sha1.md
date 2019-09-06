## [THash](../thash.md).SHA1

Creates *THash* instance implementing *SHA1* algorithm

---
### Syntax
```delphi
class function THash.SHA1: THash;
```

### Remarks

*   *SHA1* is considered **not** collision-resistant
*   *SHA1* is Merkle–Damgård hash function
*   *SHA1* digest size is 20 bytes (160 bits)

### Examples

*   compute *SHA1* digest of a file:
```delphi
procedure CalcSHA1(const FileName: string);
begin
  Writeln('SHA1:  ', THash.SHA1.UpdateFile(FileName).Digest.ToHex);
end;
```
