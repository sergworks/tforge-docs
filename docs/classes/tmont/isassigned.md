## TMont.IsAssigned

Checks if *TMont* variable is instantiated

---

### Syntax
```delphi
function TMont.IsAssigned: Boolean;
```

### Remarks

*   *TMont* variable is instantiated by `TMont.GetInstance` and uninstantiated by `TMont.Free`.

## Example:
```delphi
// demonstrates what Free and IsAssigned are doing
procedure FreeExample;
var
  Mont: TMont;

begin
  Writeln(Mont.IsAssigned);     // FALSE
  Mont:= TMont.GetInstance(37);
  Writeln(Mont.IsAssigned);     // TRUE
  Mont.Free;
  Writeln(Mont.IsAssigned);     // FALSE
end;
```
