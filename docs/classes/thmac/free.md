## [THMAC](../thmac.md).Free

Uninstantiates *THMAC* variable

---
### Syntax
```delphi
procedure THMAC.Free;
```

### Remarks

*   There is no need to call *THMAC.Free* unless a *THMAC* variable is declared as a global variable.

### See also

*   [IsAssigned](isassigned.md)

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
