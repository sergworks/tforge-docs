## ByteArray.SubBytes

Bytewise (modulo 256) subtraction of two *ByteArray* instances

---

### Syntax
```delphi
class function ByteArray.SubBytes(const A, B: ByteArray): ByteArray;
```

### Parameters

*   *A* - left *ByteArray* instance 
*   *B* - right *ByteArray* instance

### Remarks

*   the *ByteArray* operands must have equal length

### Example
```delphi
var
  A, B: ByteArray;

begin
  A:= ByteArray.FromBytes([1, 2, 3, 4]);
  B:= ByteArray.FromBytes([2, 4, 6, 2]);
  Writeln(ByteArray.SubBytes(A, B).ToString);  // outputs '255 254 253 2'
end;
```
