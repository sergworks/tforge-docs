## [THash](../thash.md).DigestSize

Returns size of message digest in bytes

---
### Syntax
```delphi
function THash.DigestSize: Integer;
```
### Examples
```delphi
begin
  Writeln('SHA256 digest size is ', THash.SHA256.DigestSize, ' bytes.');
end;
```
