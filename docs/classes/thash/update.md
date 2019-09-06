## [THash](../thash.md).Update

Processes data and updates state of *THash* instance

---
### Syntax
```delphi
function THash.Update(const Data; DataSize: Cardinal): THash;
function THash.Update(const Data: ByteArray): THash;
```

### Parameters
*   *Data*: data to be hashed
*   *DataSize*: Size of _Data_ in bytes

### Remarks
*   `THash.Update` does the same as `THash.UpdateInstance` but supports also fluent coding.

### See also
*   [THash.Update](update.md)

### Examples
*  compute *SHA256* digest of concatenated initialization vector (IV) and a file: 
```delphi
function IVFileDigest(const IV: ByteArray; const FileName: string): ByteArray;
begin
  Result:= THash.SHA256
                .Update(IV)        // or .UpdateData(IV.Raw^, IV.Len)
                .UpdateFile(FileName)
                .Digest;
end;
```
