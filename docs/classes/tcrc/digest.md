## TCRC.Digest

Returns final CRC digest and resets the shift register

---

### Syntax
```delphi
function TCRC.Digest: UInt64;
```

### Example
```delphi
var
  CRC: TCRC;
  Data: ByteArray;

begin
  Data:= ByteArray.FromText('123456789');
  CRC:= TCRC.CRC32;
  CRC.Update(Data.Raw^, Data.Len);
  Writeln(IntToHex(CRC.Digest, 8));   // output the final digest

// the same digest can be obtained by
  Writeln(IntToHex(CRC.Hash(Data), 8));
end;
```
