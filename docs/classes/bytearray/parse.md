## ByteArray.Parse

Converts string representation of bytes to equivalent *ByteArray* instance

---

### Syntax
```delphi
class function ByteArray.Parse(const S: string): ByteArray;
class function ByteArray.Parse(const S: string; Delimiter: Char): ByteArray;
```

### Parameters

*   *S*: string containing array of bytes to convert
*   *Delimiter*: character that can separate bytes in the string

### Remarks

*   if the *Delimiter* parameter is absent, the string bytes should be separated by spaces
*   if the *Delimiter* parameter is present, the string bytes can be separated by spaces and the *Delimiter*
*   the string bytes can be decimal, Pascal-style hexadecimal (*$??*) or C-style hexadecimal (*0x??*)

### Example
```delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10, 20, 30, 40', ',');
  Writeln(A.ToString);  // outputs '10 20 30 40'
  A:= ByteArray.Parse('0 $FA 0xFE 3');
  Writeln(A.ToString);  // outputs '0 250 254 3'
```
