### Array of bytes stored in a *ByteArray* instance ###

## Syntax:
```
#!delphi
property Bytes[Index: Integer]: Byte read GetByte write SetByte; default;
```

## Remarks:

*   `ByteArray.RawData` provides faster access to the *ByteArray* bytes
*   *ByteArray* bytes can also be enumerated using `for .. in` loop

## Example:
```
#!delphi
var
  A: ByteArray;
  I, Sum: Integer;
  P: PByte;
  B: Byte;

begin
  A:= ByteArray.Parse('10 20 30 40 50');
                  // using 'Bytes' property
  Sum:= 0;
  for I:= 0 to A.Len - 1 do
    Inc(Sum, A[I]);
  Writeln(Sum);
                  // using 'RawData' property
  Sum:= 0;
  P:= A.RawData;
  for I:= 0 to A.Len - 1 do
    Inc(Sum, P[I]);
  Writeln(Sum);
                  // using 'for .. in' loop
  Sum:= 0;
  for B in A do
    Inc(Sum, B);
  Writeln(Sum);
```