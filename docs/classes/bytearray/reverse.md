### Reverses byte order in a *ByteArray* ###

## Syntax:
```
#!delphi
function ByteArray.Reverse: ByteArray;
```

## Example:
```
#!delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10 20 30 40 50');
  Writeln(A.ToString);          // '10 20 30 40 50'
  Writeln(A.Reverse.ToString);  // '50 40 30 20 10'
end;
```
