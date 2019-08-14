## TCRC.CRC32

Initializes *TCRC* instance with CRC32 algorithm

---

### Syntax
```delphi
class function TCRC.CRC32: TCRC;
```

### Example
```delphi
begin
  Writeln(TCRC.CRC32.Hash(ByteArray.FromText('123456789')));
end;
```

