## [THMAC](../thmac.md).IsAssigned

Checks if *THMAC* variable is instantiated

---
### Syntax
```delphi
function THMAC.IsAssigned: Boolean;
```

### See also

*   [Free](free.md)

### Examples
```delphi
procedure TestAssigned;
var
  HMAC: THMAC;

begin
  Writeln(HMAC.IsAssigned);     // FALSE
  HMAC:= THMAC.SHA256;
  Writeln(HMAC.IsAssigned);     // TRUE
  HMAC.Free;
  Writeln(HMAC.IsAssigned);     // FALSE
end;
```
