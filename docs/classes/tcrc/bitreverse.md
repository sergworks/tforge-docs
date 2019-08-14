## TCRC.BitReverse

Reverses bit order

---

### Syntax
```delphi
class function TCRC.BitReverse(AValue: UInt64; ABitSize: Cardinal): UInt64;
```

### Parameters

*   *AValue* - a value to be bit-reversed 
*   *ABitSize* - number of bits in the *AValue*, 1..64

### Example
```delphi
var
  L: Cardinal;

begin
  L:= $12345678;
  Writeln(IntToHex(TCRC.BitReverse(L, SizeOf(L)*8), 8));
end;
```
