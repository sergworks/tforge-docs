## TCRC.Hash

Processes input data, returns final CRC digest and resets the shift register

---

### Syntax
```delphi
function TCRC.Hash(const Data; DataSize: Cardinal): UInt64;
function TCRC.Hash(const Data: ByteArray): UInt64;
```

### Parameters

*   *Data*: input data to be processed
*   *DataSize*: number of bytes in the *Data*

### Example
```delphi
var
  CRC: TCRC;
  Data: ByteArray;

begin
  Data:= ByteArray.FromText('123456789');
  CRC:= TCRC.CRC32;
  Writeln(IntToHex(CRC.Hash(Data.Raw^, Data.Len), 8));
// or
  Writeln(IntToHex(CRC.Hash(Data), 8));
end;
```
