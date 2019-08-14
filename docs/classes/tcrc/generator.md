## TCRC.Generator

Generator polynomial in bit-reversed form

---

### Syntax
```delphi
property TCRC.Generator: UInt64;
```

### Example
```delphi
var
  CRC: TCRC;

begin
  CRC:= TCRC.CRC32;
  Writeln(IntToHex(CRC.Generator, 8));   // EDB88320
end;
```
