### Converts hexadecimal representation of bytes to equivalent *ByteArray* instance ###

## Syntax:
```
#!delphi
class function ByteArray.ParseHex(const S: string): ByteArray;
class function ByteArray.ParseHex(const S: string; Delimiter: Char): ByteArray;
```

##Parameters:

*   *S*: string containing array of bytes to convert
*   *Delimiter*: character that can separate bytes in the string

##Remarks:
*   each byte in the hexadecimal string takes 2 places, like *04*
*   if the *Delimiter* parameter is absent, the string have no byte separators
*   if the *Delimiter* parameter is present, the string bytes can be separated by spaces and the *Delimiter* or can have no separators

##Example:
```
#!delphi

var
  A: ByteArray;

begin
  A:= ByteArray.ParseHex('0f1f2f3f4f');
  Writeln(A.ToString);    // outputs '15 31 47 63 79'
  A:= ByteArray.ParseHex('0f1f2f3f4f', ',');
  Writeln(A.ToString);    // outputs '15 31 47 63 79'
  A:= ByteArray.ParseHex('0f1f2f, 3f4f', ',');
  Writeln(A.ToString);    // outputs '15 31 47 63 79'

```