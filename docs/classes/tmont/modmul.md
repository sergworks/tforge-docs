## TMont.ModMul

Modular multiplication of two numbers

---

### Syntax
```delphi
function TMont.ModMul(const A, B: BigInteger): BigInteger;
```

### Remarks

*   Multiplication in Montgomery form is different from ordinary modular multiplication
*   *ModMul* implements ordinary modular multiplication using Montgomery arithmetic
*   For multiplication in Montgomery form use *Multiply*
*   The operands *A* and *B* should be in range 0..*Modulus*-1

### Example
```delphi
// demonstrates what Multiply and ModMul are doing
procedure MulExample;
var
  Mont: TMont;
  A, B, C1, C2, C3: BigInteger;

begin
  C1:= (22 * 32) mod 37;
  Writeln('(22 * 32) mod 37 = ', C1.ToString);

  Mont:= TMont.GetInstance(37);
  A:= Mont.Convert(22);   // convert 22 into Montgomery form
  B:= Mont.Convert(32);   // convert 32 into Montgomery form
// multiply in Montgomery form and convert product out of Montgomery form
  C2:= Mont.Reduce(Mont.Multiply(A, B));
  Assert(C1 = C2);

  C3:= Mont.ModMul(22, 32);
  Assert(C1 = C3);
end;
```
