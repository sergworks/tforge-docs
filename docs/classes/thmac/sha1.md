## [THMAC](../thmac.md).SHA1

Creates *THMAC* instance implementing *HMAC-SHA1* algorithm

---
### Syntax
```delphi
class function THMAC.SHA1: THMAC;
```
### Examples

*   compute *HMAC-SHA1* authentication code for a file:
```delphi
procedure CalcHMAC_SHA1(const Key: ByteArray; const FileName: string);
begin
  Writeln('HMAC-SHA1:  ', THMAC.SHA1.Init(Key).UpdateFile(FileName).Digest.ToHex);
end;
```
