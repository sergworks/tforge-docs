## TMont.GetInstance

Creates *TMont* instance

---

### Syntax
```
class function TMont.GetInstance(const Modulus: BigInteger): TMont;
```

### Remarks

*   *Modulus* should be positive odd number, otherwise exception is raised.

### Examples

```delphi
// demonstrates what ModMul is doing
procedure ModMulExample;
var
  Mont: TMont;
  A, B: BigInteger;

begin
  A:= (12 * 23) mod 37;
  Writeln('(12 * 23) mod 37 = ', A.ToString);
  Mont:= Mont.GetInstance(37);
  B:= Mont.ModMul(12, 23);
  Assert(A = B);
end;
```
