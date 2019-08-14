## TCRC.Update

Updates state of the shift register after processing input data

---

### Syntax
```delphi
procedure TCRC.Update(const Data; DataSize: Cardinal);
```

### Parameters

*   *Data*: input data to be processed
*   *DataSize*: number of bytes in the *Data*

### Example
```delphi
var
  CRC: TCRC;
  Data: ByteArray;
  P: PByte;

begin
  Data:= ByteArray.FromText('123456789');
  P:= Data.Raw;
  CRC:= TCRC.CRC32;
  CRC.Update(P^, 5);                  // process first 5 bytes
  CRC.Update((P + 5)^, 4);            // process last 4 bytes
  Writeln(IntToHex(CRC.Digest, 8));   // output the final digest

// the same digest can be obtained by
  Writeln(IntToHex(CRC.Hash(Data), 8));
```
