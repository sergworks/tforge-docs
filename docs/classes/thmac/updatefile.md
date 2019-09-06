## [THMAC](../thmac.md).UpdateFile

Processes data stored in a file and updates state of *THMAC* instance

---
### Syntax
```delphi
function THMAC.UpdateFile(const FileName: string): THMAC;
function THMAC.UpdateFile(const FileName: string; BufSize: Integer): THMAC;
```

### Parameters
*   *FileName*: name of a file to be processed
*   *BufSize*: optional read buffer size

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
