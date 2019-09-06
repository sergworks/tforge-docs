## TMont.Add

Modular addition of two numbers

---

### Syntax
```delphi
function TMont.Add(const A, B: BigInteger): BigInteger;
```

### Remarks

*   Addition in Montgomery form is the same as ordinary modular addition
*   The operands *A* and *B* should be in range 0..*Modulus*-1

### Example
```delphi
// demonstrates what Add and Subtract are doing
procedure AddExample;
var
  Mont: TMont;
  A, B, C: BigInteger;

begin
  Mont:= TMont.GetInstance(37);
  A:= 22;
  B:= Mont.Add(A, 32);
  Writeln(A.ToString, ' + 32 = ', B.ToString, ' (mod 37)');
  C:= Mont.Subtract(B, 32);
  Writeln(B.ToString, ' - 32 = ', C.ToString, ' (mod 37)');
  Assert(A = C);
end;

```
