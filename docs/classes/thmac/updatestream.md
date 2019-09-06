## [THMAC](../thmac.md).UpdateStream

Processes data stored in a stream and updates state of *THMAC* instance

---
### Syntax
```delphi
function THMAC.UpdateStream(Stream: TStream): THMAC;
function THMAC.UpdateStream(Stream: TStream; BufSize: Integer): THMAC;
```

### Parameters
*   *Stream*: stream to be pcocessed
*   *BufSize*: optional size of read buffer

### Examples
*  compute *HMAC-SHA256* digest of concatenated initialization vector (IV) and a file: 
```delphi
function IVFileHMAC(const Key: ByteArray; const IV: ByteArray; Stream: TStream): ByteArray;
begin
  Result:= THash.SHA256
                .Init(Key)
                .Update(IV)        // or .UpdateData(IV.Raw^, IV.Len)
                .UpdateStream(Stream)
                .Digest;
end;
```
