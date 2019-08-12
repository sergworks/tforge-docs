### Pointer to bytes stored in a *ByteArray* instance ###

## Syntax:
```
#!delphi
property RawData: PByte read GetRawData;
```

## Remarks:

*   `ByteArray.RawData` provides fast access to the *ByteArray* bytes

## Example:
```
#!delphi
var
  A: ByteArray;
  P: PByte;

begin
  A:= ByteArray.Parse('10 20 30 40 50');
  Writeln(A.ToString);  // 10 20 30 40 50
  A.RawData[3]:= 80;
  Writeln(A.ToString);  // 10 20 30 80 50
```