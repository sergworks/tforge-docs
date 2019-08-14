## ByteArray.Len

Number of bytes in a *ByteArray* instance

---

### Syntax
```delphi
property Len: Integer read GetLen write SetLen;
```

### Remarks

*   number of bytes set by `ByteArray.Len` must not exceed size of *ByteArray* instance

### Example
```delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10 20 30 40 50');
  Writeln(A.Len, ': ', A.ToString);  // '5: 10 20 30 40 50'
  A.Len:= 4;
  Writeln(A.Len, ': ', A.ToString);  // '4: 10 20 30 40'
  A.Len:= 5;
  Writeln(A.Len, ': ', A.ToString);  // '5: 10 20 30 40 50'
```
