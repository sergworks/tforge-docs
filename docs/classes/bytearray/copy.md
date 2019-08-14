## ByteArray.Copy

Copies *ByteArray* instance

---

### Syntax
```delphi
class function ByteArray.Copy(const A: ByteArray; I: Cardinal): ByteArray;
class function ByteArray.Copy(const A: ByteArray; I, L: Cardinal): ByteArray;
```

### Parameters

*   *A* - source *ByteArray*
*   *I* - starting index to copy from 
*   *L* - number of bytes to be copied

### Remarks

*   if one parameter is used, the array bytes are copied starting from the index *I* till the end of the array
*   if two parameters are used, the *L* bytes are copied starting from the index *I*
*   if *I + L* is greater than the array length, the bytes are copied starting from the index *I* till the end of the array

### Example
```delphi
var
  A, B: ByteArray;

begin
  A:= ByteArray.Parse('10, 20, 30, 40, 50', ',');
  Writeln(A.ToString);  // outputs '10 20 30 40 50'
  B:= ByteArray.Copy(A, 1, 2);
  Writeln(B.ToString);  // outputs '20 30'
end;
```
