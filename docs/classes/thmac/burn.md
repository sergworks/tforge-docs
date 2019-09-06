## [THMAC](../thmac.md).Burn

Erases data stored in *THMAC* instance

---
### Syntax
```delphi
procedure THMAC.Burn;
```
### Examples

*   Compute HMAC-SHA1 of a file _FileName_ and burn any confidential data:
```delphi
function GetHMAC(const Password: ByteArray): ByteArray;
var
  HMAC: THMAC;

begin
  HMAC:= THMAC.SHA1;
  try
    Result:= HMAC.Init(Password).UpdateFile(FileName).Digest;
  finally
    HMAC.Burn;
  end;
end;
```
