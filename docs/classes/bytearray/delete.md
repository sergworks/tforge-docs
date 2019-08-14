## ByteArray.Delete

Deletes bytes from *ByteArray* instance

---

### Syntax
```delphi
class procedure ByteArray.Delete(const A: ByteArray; I, L: Cardinal);
```

### Parameters

*   *A* - source *ByteArray*
*   *I* - starting index to delete bytes 
*   *L* - number of bytes to be deleted

### Example
```delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10 20 30 40 50', ' ');
  Writeln(A.ToString);  // '10 20 30 40 50'
  ByteArray.Delete(A, 1, 2);
  Writeln(A.ToString);  // '10 40 50'
  ByteArray.Delete(A, 0, 1);
  Writeln(A.ToString);  // '40 50'
end;
```
