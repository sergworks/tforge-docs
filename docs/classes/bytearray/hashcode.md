## TByteArray.HashCode

Returns 32-bit hash value for *ByteArray* instance

---

### Syntax
```delphi
function ByteArray.HashCode: Integer;
```

### Remarks

*   Hash code can be used to build hash tables (aka dictionaries, associative arrays) having *ByteArray* values as keys

### Example
```delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10 20 30 40 50');
  Writeln(IntToHex(A.HashCode, 8));
  A:= ByteArray.Parse('10 20 30 40 50 60');
  Writeln(IntToHex(A.HashCode, 8));
end;
```
