### Fills the bytes of a *ByteArray* instance by a given value ###

## Syntax:
```
#!delphi
procedure ByteArray.Fill(AValue: Byte);
```

## Parameters:

*   *AValue* - byte to fill the *ByteArray*

## Example:
```
#!delphi
var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10 20 30');
  Writeln(A.ToString);  // outputs '10 20 30'
  A.Fill(40);
  Writeln(A.ToString);  // outputs '40 40 40'
```
