## [THMAC](../thmac.md).MD5

Creates *THMAC* instance implementing *HMAC-MD5* algorithm

---
### Syntax
```delphi
class function THMAC.MD5: THMAC;
```
### Examples

*   compute *HMAC-MD5* authentication code for a file:
```delphi
procedure CalcHMAC_MD5(const Key: ByteArray; const FileName: string);
begin
  Writeln('HMAC-MD5:  ', THMAC.MD5.Init(Key).UpdateFile(FileName).Digest.ToHex);
end;
```
