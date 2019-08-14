## ByteArray.Insert

Inserts bytes into *ByteArray* instance

---

### Syntax
```delphi
class function ByteArray.Insert(const A: ByteArray; I: Cardinal; B: Byte): ByteArray;
class function ByteArray.Insert(const A: ByteArray; I: Cardinal; const B: ByteArray): ByteArray;
class function ByteArray.Insert(const A: ByteArray; I: Cardinal; const B: TBytes): ByteArray;
```

### Parameters

*   *A* - source *ByteArray*
*   *I* - starting index to insert from 
*   *B* - bytes to be inserted

### Example
```delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10 20 30', ' ');
  Writeln(A.ToString);  // '10 20 30'
  Writeln(ByteArray.Insert(A, 1, 255).ToString);  // '10 255 20 30'
  Writeln(ByteArray.Insert(A, 1, ByteArray.Parse('100 101')).ToString);  // '10 100 101 20 30'
end;
```
