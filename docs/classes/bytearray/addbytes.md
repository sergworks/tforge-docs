### Bytewise (modulo 256) addition of two *ByteArray* instances ###

## Syntax:
```
#!delphi
 class function ByteArray.AddBytes(const A, B: ByteArray): ByteArray;
```

## Parameters:

*   *A* - left *ByteArray* instance 
*   *B* - right *ByteArray* instance

## Remarks:

*   if the *ByteArray* operands have different lengths, the result has length of the shorter operand 

## Example:
```
#!delphi

var
  A, B: ByteArray;

begin
  A:= ByteArray.FromBytes([1, 2, 3, 4, 5]);
  B:= ByteArray.FromBytes([10, 20, 30]);
  Writeln(ByteArray.AddBytes(A, B).ToString);  // outputs '11 22 33'
```