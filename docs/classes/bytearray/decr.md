### Decrements integer value stored in a *ByteArray* instance ###

## Syntax:
```
#!delphi
procedure ByteArray.Decr;
```

## Remarks:

*   `ByteArray.Decr` assumes that the bytes stored in a *ByteArray* instance is a non-negative integer value in big-endian format

## Example:
```
#!delphi
var
  A: ByteArray;

begin
  A:= ByteArray.ParseHex('00 00 01', ' ');
  Writeln(A.ToHex);  // outputs 000001
  A.Decr;
  Writeln(A.ToHex);  // outputs 000000
  A.Decr;
  Writeln(A.ToHex);  // outputs FFFFFF
```