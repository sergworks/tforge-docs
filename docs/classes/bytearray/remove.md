## ByteArray.Remove

Removes bytes from a *ByteArray*

---

### Syntax
```delphi
class function ByteArray.Remove(const A: ByteArray; I: Cardinal): ByteArray;
class function ByteArray.Remove(const A: ByteArray; I, L: Cardinal): ByteArray;
```

### Parameters
*   *A* - source *ByteArray*
*   *I* - starting index to remove from 
*   *L* - number of bytes to be removed

### Example
```delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10 20 30 40 50');
  Writeln(A.ToString);  // '10 20 30 40 50'
  Writeln(ByteArray.Remove(A, 1, 2).ToString);  // '10 40 50'
  Writeln(ByteArray.Remove(A, 2, 2).ToString);  // '10 20 50'
end;
```
