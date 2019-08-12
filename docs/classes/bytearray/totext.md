### Converts a *ByteArray* variable to text string ###

## Syntax:
```
#!delphi
function ByteArray.ToText: string;
```

##Remarks:

*   the *ByteArray* contents is interpreted as a *UTF8* string; ex the byte *97 ($61)* in the *ByteArray* becomes the latin 'a' character in the result string. 

##See also:
*   [ByteArray.FromText](FromText)

##Example:
```
#!delphi

var
  A: ByteArray;

begin
  A:= ByteArray.Parse('72 101 108 108 111 44 32 87 111 114 108 100 33');
  Writeln(A.ToText);    // 'Hello, World!'
```