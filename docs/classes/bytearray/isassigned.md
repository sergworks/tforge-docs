### Checks if a *ByteArray* variable is instantiated

## Syntax:
```
#!delphi
function ByteArray.IsAssigned: Boolean;
```

## Example:
```
#!delphi
var
  A: ByteArray;

begin
  Writeln(A.IsAssigned);   // False
  A:= ByteArray.Allocate(20);
  Writeln(A.IsAssigned);   // True
  A.Free;
  Writeln(A.IsAssigned);   // False
end;
```