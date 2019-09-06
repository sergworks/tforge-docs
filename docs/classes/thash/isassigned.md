## [THash](../thash.md).IsAssigned

Checks if *THash* variable is instantiated

---
### Syntax
```delphi
function THash.IsAssigned: Boolean;
```

### See also

*   [Free](free.md)

### Examples
```delphi
procedure TestAssigned;
var
  SHA256: THash;

begin
  Writeln(SHA256.IsAssigned);     // FALSE
  SHA256:= THash.SHA256;
  Writeln(SHA256.IsAssigned);     // TRUE
  SHA256.Free;
  Writeln(SHA256.IsAssigned);     // FALSE
end;
```
