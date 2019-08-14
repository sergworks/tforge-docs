## ByteArray.Concat

Concatenates two *ByteArray* operands

---

### Syntax
```delphi
class function ByteArray.Concat(const A, B: ByteArray): ByteArray;
```

### Parameters

*   *A* - left *ByteArray* instance 
*   *B* - right *ByteArray* instance

### Remarks

*   *ByteArray* operands can also be concatenated using addition operator (+)

### Example
```delphi
var
  A, B: ByteArray;

begin
  A:= ByteArray.FromBytes([1, 2, 3]);
  B:= ByteArray.FromBytes([10, 20, 30]);
  Writeln(ByteArray.Concat(A, B).ToString);  // outputs '1 2 3 10 20 30'
  Writeln((A + B).ToString);                 // outputs '1 2 3 10 20 30'
end;
```
