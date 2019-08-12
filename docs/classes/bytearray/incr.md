### Increments integer value stored in a *ByteArray* instance ###

## Syntax:
```
#!delphi
procedure ByteArray.Incr;
```

## Remarks:

*   `ByteArray.Incr` assumes that the bytes stored in a *ByteArray* instance is a non-negative integer value in big-endian format

## Example:
```
#!delphi
var
  A: ByteArray;

begin
  A:= ByteArray.ParseHex('ff ff ff', ' ');
  Writeln(A.ToHex);  // outputs FFFFFF
  A.Incr;
  Writeln(A.ToHex);  // outputs 000000
  A.Incr;
  Writeln(A.ToHex);  // outputs 000001
```