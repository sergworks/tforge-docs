## ByteArray.Raw

Pointer to bytes stored in a *ByteArray* instance

---

### Syntax
```delphi
function ByteArray.Raw: PByte;
```

### Remarks

*   `ByteArray.Raw` provides fast access to the *ByteArray* bytes

### Example
```delphi
var
  A: ByteArray;
  P: PByte;

begin
  A:= ByteArray.Parse('10 20 30 40 50');
  Writeln(A.ToString);  // 10 20 30 40 50
  A.Raw[3]:= 80;
  Writeln(A.ToString);  // 10 20 30 80 50
end;
```
