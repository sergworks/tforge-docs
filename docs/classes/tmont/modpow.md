## TMont.ModPow

Modular exponentiation

---

### Syntax
```delphi
function TMont.ModPow(const Base: BigInteger; Pow: TLimb): BigInteger;
function TMont.ModPow(const Base, Pow: BigInteger): BigInteger;
```

### Parameters
*   *Base* - Number to raise to the *Pow* power.
*   *Pow* - Exponent to raise *Base* by.

### Remarks

*   The operand *Base* should be in range 0..*Modulus*-1

### Example
```delphi
// demonstrates what ModPow is doing
procedure PowExample;
var
  Mont: TMont;
  C1, C2: BigInteger;

begin
  C1:= BigInteger.ModPow(22, 32, 37);   // 22^32 mod 37
  Writeln('22^32 mod 37 = ', C1.ToString);

  Mont:= TMont.GetInstance(37);
  C2:= Mont.ModPow(22, 32);

  Assert(C1 = C2);
end;
```
