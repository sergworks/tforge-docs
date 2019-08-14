## ByteArray.Clone

Clones *ByteArray* instance

---

### Syntax
```delphi
function ByteArray.Clone: ByteArray;
```

### Remarks

*   `ByteArray.Clone` method creates a new *ByteArray* instance; the *ByteArray* assignment increments the reference count of the same instance. The difference is illustrated by the example below

### Example
```delphi
var
  A, B, C: ByteArray;

begin
  A:= ByteArray.Parse('10, 20, 30, 40', ',');
  Writeln(A.ToString);  // outputs '10 20 30 40'
  B:= A.Clone;
  C:= A;
  A[0]:= 255;
  Writeln(A.ToString);  // outputs '255 20 30 40'
  Writeln(B.ToString);  // outputs '10 20 30 40'
  Writeln(C.ToString);  // outputs '255 20 30 40'
end;
```
