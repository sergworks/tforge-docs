## ByteArray.TryParseHex

Converts hexadecimal representation of bytes to equivalent *ByteArray* instance

---

### Syntax
```delphi
class function ByteArray.TryParseHex(const S: string; var R: ByteArray): Boolean;
class function ByteArray.TryParseHex(const S: string; Delimiter: Char; var R: ByteArray): Boolean;
```

### Parameters

*   *S*: string containing array of bytes to convert
*   *Delimiter*: character that can separate bytes in the string
*   *R*: resulting *ByteArray* instance 

### Return Value

*   *True*: if the string is parsed successfully
*   *False*: otherwise

### Remarks
*   each byte in the hexadecimal string takes 2 places, like *04*
*   if the *Delimiter* parameter is absent, the string have no byte separators
*   if the *Delimiter* parameter is present, the string bytes can be separated by spaces and the *Delimiter* or can have no separators

### Example
```delphi
var
  A: ByteArray;

begin
  if ByteArray.TryParseHex('0f1f2f3f4f', A)
    then Writeln(A.ToString)    // outputs '15 31 47 63 79'
    else Writeln('! String Parsing Error');
end;
```
