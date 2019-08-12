### Duplicates a *ByteArray* instance ###

## Syntax:
```
#!delphi
function ByteArray.Copy: ByteArray;
function ByteArray.Copy(I: Cardinal): ByteArray;
function ByteArray.Copy(I, L: Cardinal): ByteArray;
```

## Parameters:

*   *I* - starting index to copy from 
*   *L* - number of bytes to be copied

## Remarks:

*   if no parameters are used, the whole byte array is copied
*   if one parameter is used, the array bytes are copied starting from the index *I* till the end of the array
*   if two parameters are used, the *L* bytes are copied starting from the index *I*
*   if *I + L* is greater than the array length, the bytes are copied starting from the index *I* till the end of the array
*   the `ByteArray.Copy` method creates a new *ByteArray* instance; the *ByteArray* assignment increments the reference count of the same instance. The difference is illustrated by the example below

## Example:
```
#!delphi

var
  A, B, C: ByteArray;

begin
  A:= ByteArray.Parse('10, 20, 30, 40', ',');
  Writeln(A.ToString);  // outputs '10 20 30 40'
  B:= A.Copy;
  C:= A;
  A[0]:= 255;
  Writeln(A.ToString);  // outputs '255 20 30 40'
  Writeln(B.ToString);  // outputs '10 20 30 40'
  Writeln(C.ToString);  // outputs '255 20 30 40'

```