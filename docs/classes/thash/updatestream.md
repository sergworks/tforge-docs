## [THash](../thash.md).UpdateStream

Processes data stored in stream and updates state of *THash* instance

---
### Syntax
```delphi
function THash.UpdateStream(Stream: TStream): THash;
function THash.UpdateStream(Stream: TStream; BufSize: Integer): THash;
```

### Parameters
*   *Stream*: stream to be hashed
*   *BufSize*: optional size of read buffer

### Examples
*  compute *SHA256* digest of concatenated initialization vector (IV) and a stream: 
```delphi
function IVFileDigest(const IV: ByteArray; Stream: TStream): ByteArray;
begin
  Result:= THash.SHA256
                .Update(IV)
                .UpdateStream(Stream)
                .Digest;
end;
```
