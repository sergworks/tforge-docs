### Number of bytes in a *ByteArray* instance ###

## Syntax:
```
#!delphi
property Len: Integer read GetLen write SetLen;
```

## Remarks:

*   setting `ByteArray.Len` may reallocate the *ByteArray* instance in memory

## Example:
```
#!delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10 20 30 40 50');
  Writeln(A.Len, ': ', A.ToString);  // 5: 10 20 30 40 50
  A.Len:= 6;
  A[5]:= 60;
  Writeln(A.Len, ': ', A.ToString);  // 6: 10 20 30 40 50 60
```