## ByteArray.ReAlloc

Reallocates *ByteArray* instance in memory

---

### Syntax
```delphi
class procedure ByteArray.ReAlloc(var A: ByteArray; ASize: Cardinal);
```

### Parameters

*   *ASize*: number of bytes allocated for a new *ByteArray* instance

### Remarks

*   `ByteArray.ReAlloc` creates a new *ByteArray* instance with the reference count = *1* and copies the data from the old instance to the new instance.

### Example
```delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10 20 30 40');
  Writeln(A.Len);                            // 4
  ByteArray.Realloc(A, 12);
  Writeln(A.Len);                            // 12
  Writeln(ByteArray.Copy(A, 0, 4).ToString); // '10 20 30 40'
end;
```
