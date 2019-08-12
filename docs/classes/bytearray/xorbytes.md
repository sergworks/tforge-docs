### Bitwise *xor* of two *ByteArray* operands ###

## Syntax:
```
#!delphi
class function ByteArray.XorBytes(const A, B: ByteArray): ByteArray;
```

## Parameters:

*   *A* - left *ByteArray* operand 
*   *B* - right *ByteArray* operand

## Remarks:

*   if the operands have different lengths, the result has the length of the shorter *ByteArray* 
*   *xor* operator can be used instead of *XorBytes* function

## Example:
```
#!delphi

var
  A, B: ByteArray;

begin
  A:= ByteArray.FromBytes([1, 2, 3]);
  B:= ByteArray.FromBytes([$10, $12, $14]);
  Writeln(ByteArray.XorBytes(A, B).ToString);  // outputs '17 16 23'
  Writeln((A xor B).ToString);                 // outputs '17 16 23'
```