## [THMAC](../thmac.md).Update

Processes data and updates state of *THMAC* instance

---
### Syntax
```delphi
function THMAC.Update(const Data; DataSize: Cardinal): THMAC;
function THMAC.Update(const Data: ByteArray): THMAC;
```

### Parameters
*   *Data*: data to be processed
*   *DataSize*: Size of _Data_ in bytes

### Remarks
*   `THMAC.Update` does the same as `THMAC.UpdateInstance` but supports also fluent coding.

### Examples
*  compute *HMAC-SHA256* digest of concatenated initialization vector (IV) and a file: 
```delphi
function IVFileHMAC(const Key: ByteArray; const IV: ByteArray; const FileName: string): ByteArray;
begin
  Result:= THash.SHA256
                .Init(Key)
                .Update(IV)        // or .UpdateData(IV.Raw^, IV.Len)
                .UpdateFile(FileName)
                .Digest;
end;
```
