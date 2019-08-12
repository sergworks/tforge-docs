### Inserts bytes into a *ByteArray* ###

## Syntax:
```
#!delphi
function ByteArray.Insert(I: Cardinal; B: Byte): ByteArray;
function ByteArray.Insert(I: Cardinal; const B: ByteArray): ByteArray;
function ByteArray.Insert(I: Cardinal; const B: TBytes): ByteArray;
```

## Parameters:

*   *I* - starting index to insert from 
*   *B* - bytes to be inserted

## Example:
```
#!delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10 20 30', ' ');
  Writeln(A.ToString);  // '10 20 30'
  Writeln(A.Insert(1, 255).ToString);  // '10 255 20 30'
  Writeln(A.Insert(1, ByteArray.Parse('100 101')).ToString);  // '10 100 101 20 30'
end;
```