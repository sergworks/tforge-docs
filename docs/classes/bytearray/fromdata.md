## ByteArray.FromData

Creates new *ByteArray* instance and initializes it

---

### Syntax
```delphi
class function ByteArray.FromData(const Data; DataLen: Cardinal; Reversed: Boolean): ByteArray;
```

### Parameters

*   *Data*: buffer for initializing a new *ByteArray* instance
*   *DataLen*: size of the buffer (also length of a new *ByteArray* instance)
*   *Reversed*: if *True* then the byte order is reversed

### Remarks

*   usually the byte order is reversed to change endianness, i.e. an integer type stores bytes in the little-endian format, while *ByteArray* expects bytes in the big-endian format. 

### See also

*   [ByteArray.ToData](todata)

### Example
```delphi
var
  A: ByteArray;
  I: Cardinal;

begin
  I:= $030201;
  A:= ByteArray.FromData(I, SizeOf(I), False);
  Writeln(A.ToString);    // '1 2 3 0'
  A:= ByteArray.FromData(I, SizeOf(I), True);
  Writeln(A.ToString);    // '0 3 2 1'
end;
```
