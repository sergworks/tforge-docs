## ByteArray.AddBytes

Bytewise (modulo 256) addition of two *ByteArray* operands

---

### Syntax
```delphi
class function ByteArray.AddBytes(const A, B: ByteArray): ByteArray;
```

### Parameters

*   *A* - left *ByteArray* operand 
*   *B* - right *ByteArray* operand

### Remarks

*   the *ByteArray* operands must have equal length

### Example
```delphi
var
  A, B: ByteArray;

begin
  A:= ByteArray.FromBytes([1, 2, 3]);
  B:= ByteArray.FromBytes([254, 254, 254]);
  Writeln(ByteArray.AddBytes(A, B).ToString);  // outputs '255 0 1'
end;
```
