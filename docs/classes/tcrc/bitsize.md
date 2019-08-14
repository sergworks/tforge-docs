## TCRC.BitSize

Number of bits in CRC digest

---

### Syntax
```delphi
property TCRC.BitSize: Cardinal;
```

### Example
```delphi
var
  CRC: TCRC;

begin
  CRC:= TCRC.CRC32;
  Writeln(CRC.BitSize);   // 32
end;
```
