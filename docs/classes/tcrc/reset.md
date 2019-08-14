## TCRC.Reset

Resets the shift register

### Syntax
```delphi
procedure TCRC.Reset;
```

### Remarks

*   normally *Reset* is called implicitly; the only reason to call *Reset* explicitly is to cancel processing input data (by successive *Update* calls) without getting the digest (by the final *Digest* call)

### Example
```delphi
var
  CRC: TCRC;
  Data: ByteArray;

begin
  Data:= ByteArray.FromText('123456789');
  CRC:= TCRC.CRC32;
  CRC.Update(Data.Raw^, Data.Len);
// normally CRC.Digest should be called here which resets the shift register
//   if we don't call CRC.Digest we need CRC.Reset before reusing the CRC instance
  CRC.Reset;
  CRC.Update(Data.Raw^, Data.Len);
  Writeln(IntToHex(CRC.Digest, 8));
```
