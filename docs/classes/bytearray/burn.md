## ByteArray.Burn

Clears data stored in *ByteArray* instance

---

### Syntax
```delphi
procedure ByteArray.Burn;
```

### Example
```delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10, 20, 30, 40', ',');
  Writeln(A.ToString);  // outputs '10 20 30 40'
  A.Burn;
  Writeln(A.ToString);  // outputs '0'
end;
```
