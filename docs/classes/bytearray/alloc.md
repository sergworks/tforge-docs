### Creates a new *ByteArray* instance of a given length ###

## Syntax:
```
#!delphi
class function ByteArray.Allocate(ASize: Cardinal): ByteArray;
class function ByteArray.Allocate(ASize: Cardinal; AFiller: Byte): ByteArray;
```

##Parameters:

*   *ASize*: number of bytes allocated for a new *ByteArray* instance
*   *AFiller*: initial value of bytes in a new *ByteArray* instance

##Remarks:

*   if *Allocate* is called with a single parameter (*ASize*), the initial values are undefined.

##Example:
```
#!delphi

var
  A, B: ByteArray;

begin
  A:= ByteArray.Allocate(20);        // allocate 20 bytes
  B:= ByteArray.Allocate(20, $FF);   // allocate 20 bytes and initialize them by $FF
```