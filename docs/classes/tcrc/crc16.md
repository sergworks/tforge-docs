## TCRC.CRC16

Initializes *TCRC* instance with CRC16 algorithm

---

### Syntax
```delphi
class function TCRC.CRC16: TCRC;
```

### Example
```
begin
  Writeln(TCRC.CRC16.Hash(ByteArray.FromText('123456789')));
end;
```
