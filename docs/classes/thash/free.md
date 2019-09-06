## [THash](../thash.md).Free

Finalizes *THash* variable

---
### Syntax
```delphi
procedure THash.Free;
```

### Remarks

*   There is no need to call *THash.Free* unless a *THash* variable is declared as a global variable.

### See also

*   [IsAssigned](isassigned.md)

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
