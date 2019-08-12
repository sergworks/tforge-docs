### Removes bytes from a *ByteArray* ###

## Syntax:
```
#!delphi
function ByteArray.Remove(I: Cardinal): ByteArray;
function ByteArray.Remove(I, L: Cardinal): ByteArray;
```

## Parameters:

*   *I* - starting index to remove from 
*   *L* - number of bytes to be removed

## Example:
```
#!delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10 20 30 40 50');
  Writeln(A.ToString);  // '10 20 30 40 50'
  Writeln(A.Remove(1, 2).ToString);  // '10 40 50'
  Writeln(A.Remove(2, 2).ToString);  // '10 20 50'
end;
```