## ByteArray.Fill

Fills the bytes of a *ByteArray* instance by a given value

---

### Syntax
```delphi
class procedure ByteArray.Fill(const A: ByteArray; AValue: Byte);
```

### Parameters

*   *A* - *ByteArray* to be filled
*   *AValue* - byte to fill the *ByteArray*

### Example
```delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10 20 30');
  Writeln(A.ToString);  // outputs '10 20 30'
  ByteArray.Fill(A, 40);
  Writeln(A.ToString);  // outputs '40 40 40'
end;
```
