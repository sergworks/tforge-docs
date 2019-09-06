## [THash](../thash.md).Burn

Erases data stored in *THash* instance

---
### Syntax
```delphi
procedure THash.Burn;
```
### Examples

*   Compute SHA256 of a file _FileName_ and burn any confidential data:
```delphi
var
  SHA256: THash;

begin
  SHA256:= THash.SHA256;
  try
    Writeln(SHA256.UpdateFile(FileName).Digest.ToHex);
  finally
    SHA256.Burn;
  end;
  ...
end;
```
