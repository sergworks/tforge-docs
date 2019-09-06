## [THash](../thash.md).GetInstance

Creates *THash* instance implementing hash algorithm specified by parameter

---
### Syntax
```delphi
class function THash.GetInstance(AlgID: Integer): THash;
class function THash.GetInstance(const AlgName: string): THash;
```

### Examples

*   compute *MD5* digest of a file:
```delphi
uses
  tfHashes;

procedure CalcMD5(const FileName: string);
begin
  Writeln('MD5:  ', THash.GetInstance(ALG_MD5).UpdateFile(FileName).Digest.ToHex);
// or else
//  Writeln('MD5:  ', THash.GetInstance("md5").UpdateFile(FileName).Digest.ToHex);
// or else
//  Writeln('MD5:  ', THash.MD5.UpdateFile(FileName).Digest.ToHex);
end;
```
