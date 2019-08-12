### Bitwise *and* of two *ByteArray* operands ###

## Syntax:
```
#!delphi
class function ByteArray.AndBytes(const A, B: ByteArray): ByteArray;
```

## Parameters:

*   *A* - left *ByteArray* operand 
*   *B* - right *ByteArray* operand

## Remarks:

*   if the *ByteArray* operands have different lengths, the result has length of the shorter operand 
*   *and* operator can be used instead of *AndBytes* function

## Example:
```
#!delphi

var
  A, B: ByteArray;

begin
  A:= ByteArray.FromBytes([1, 2, 3]);
  B:= ByteArray.FromBytes([$11, $22, $31]);
  Writeln(ByteArray.AndBytes(A, B).ToString);  // outputs '1 2 1'
  Writeln((A and B).ToString);                 // outputs '1 2 1'
```