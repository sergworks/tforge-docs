## [THash](../thash.md).UpdateInstance

Processes data and updates state of *THash* instance

---
### Syntax
```delphi
procedure THash.UpdateInstance(const Data; DataSize: Cardinal);
procedure THash.UpdateInstance(const Data: ByteArray);
```

### Parameters
*   *Data*: data to be hashed
*   *DataSize*: size of *Data* in bytes

### Remarks
*   *THash.InitInstance*, *THash.UpdateInstance* and *THash.DoneInstance* methods constitute traditional (non-fluent) hash-computing API.

### See also
*   [THash.Update](update.md)

### Examples
*   compute *SHA256* digest of a data:
```delphi
procedure CalcSHA256(const Data: ByteArray);
var
  SHA256: THash;

begin
  SHA256:= THash.SHA256;
  SHA256.UpdateInstance(Data);        // or SHA256.UpdateInstance(Data.Raw^, Data.Len);
  Writeln(SHA256.Digest.ToHex);
end;
```
