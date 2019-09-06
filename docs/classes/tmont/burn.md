## TMont.Burn

Clears data stored in *TMont* instance

---

### Syntax
```delphi
procedure TMont.Burn;
```

### Examples
```delphi
// demonstrates how Burn is used
procedure BurnExample;
var
  Mont: TMont;

begin
  Mont:= TMont.GetInstance(37);
  try
    Writeln(Mont.ModMul(12, 23).ToString);
  finally
    Mont.Burn;
  end;
end;
```
