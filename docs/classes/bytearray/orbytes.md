### Bitwise *or* of two *ByteArray* operands ###

## Syntax:
```
#!delphi
class function OrBytes(const A, B: ByteArray): ByteArray;
```

## Parameters:

*   *A* - left *ByteArray* operand 
*   *B* - right *ByteArray* operand

## Remarks:

*   if the operands have different lengths, the result has the length of the shorter *ByteArray* 
*   *or* operator can be used instead of *OrBytes* function

## Example:
```
#!delphi

var
  A, B: ByteArray;

begin
  A:= ByteArray.FromBytes([1, 2, 3]);
  B:= ByteArray.FromBytes([$10, $20, $30]);
  Writeln(OrBytes(A, B).ToString);  // outputs '17 34 51'
  Writeln((A or B).ToString);       // outputs '17 34 51'
```