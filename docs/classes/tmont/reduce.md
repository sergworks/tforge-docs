## TMont.Reduce

Converts a number out of Montgomery form

---

### Syntax
```delphi
function TMont.Reduce(const A: BigInteger): BigInteger;
```

### Example
```delphi
// demonstrates what Convert and Reduce are doing
procedure ConvertExample;
var
  Mont: TMont;
  A, B, C: BigInteger;

begin
  Mont:= TMont.GetInstance(37);
  A:= 12;
  B:= Mont.Convert(A);
  Writeln(A.ToString, ' in Montgomery form = ', B.ToString);
  C:= Mont.Reduce(B);
  Assert(A = C);
end;
```
