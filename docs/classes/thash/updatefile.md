## [THash](../thash.md).UpdateFile

Processes data stored in file and updates state of *THash* instance

---
### Syntax
```delphi
function THash.UpdateFile(const FileName: string): THash;
function THash.UpdateFile(const FileName: string; BufSize: Integer): THash;
```

### Parameters
*   *FileName*: name of file to be hashed
*   *BufSize*: optional read buffer size

### Examples
*  compute *SHA256* digest of concatenated initialization vector (IV) and a file: 
```delphi
function IVFileDigest(const IV: ByteArray; const FileName: string): ByteArray;
begin
  Result:= THash.SHA256
                .Update(IV)
                .UpdateFile(FileName)
                .Digest;
end;
```
