## TMont.Free

Uninstantiates *TMont* variable

---

### Syntax
```delphi
procedure TMont.Free;
```

### Remarks

*   *TMont* instance is freed from memory when its reference count reaches zero.
*   There is no need to call `TMont.Free` explicitly; the instance is freed automatically when all variables referencing it go out of scope.

### Example
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
