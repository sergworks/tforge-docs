## THash

Implements hash algorithms; declared in _tfHashes_ unit

---
### Class Methods
| Method       | Description   |
|--------------|---------------|
[MD5](thash/md5.md)          | Creates *THash* instance implementing *MD5* algorithm
[SHA1](thash/sha1.md)        | Creates *THash* instance implementing *SHA1* algorithm
[SHA224](thash/sha224.md)    | Creates *THash* instance implementing *SHA224* algorithm
[SHA256](thash/sha256.md)    | Creates *THash* instance implementing *SHA256* algorithm
[SHA384](thash/sha384.md)    | Creates *THash* instance implementing *SHA384* algorithm
[SHA512](thash/sha512.md)    | Creates *THash* instance implementing *SHA512* algorithm
[GetInstance](thash/getinstance.md) | Creates *THash* instance
[GetIDByName](thash/getidbyname.md) | Converts hash algorithm name to ID
[GetNameByID](thash/getnamebyid.md) | Converts hash algorithm ID to name

### Instance Methods
| Method       | Description   |
|--------------|---------------|
[Burn](thash/burn.md)          | Erases data stored in *THash* instance
[Clone](thash/clone.md)        | Clones *THash* instance
[DeriveKey](thash/derivekey.md)| Derives key from password using PBKDF1 algorithm
[Digest](thash/digest.md) | Returns message digest
[DigestSize](thash/digestsize.md)   | Returns size of message digest
[DoneInstance](thash/doneinstance.md)     | Outputs message digest
[Free](thash/free.md)     | Uninstantiates *THash* variable
[GetDigest](thash/getdigest.md)     | Outputs a message digest
[InitInstance](thash/initinstance.md)     | Initializes *THash* instance state
[IsAssigned](thash/isassigned.md)   | Checks if *THash* variable is instantiated
[UpdateInstance](thash/updateinstance.md)         | Processes data and updates *THash* instance state
[Update](thash/update.md) | Processes data and updates *THash* instance state
[UpdateFile](thash/updatefile.md) | Processes file and updates *THash* instance state
[UpdateStream](thash/updatestream.md) | Processes stream and updates *THash* instance state

---

### Examples

*   Compute *SHA256* digest of concatenated initialization vector (IV) and file: 
```delphi
function IVFileDigest(const IV: ByteArray; const FileName: string): ByteArray;
begin
  Result:= THash.SHA256
                .Update(IV)
                .UpdateFile(FileName)
                .Digest;
end;
```

*   Compute *MD5* and *SHA1* digests of a file in a single pass; the example also demonstrates the use of *Burn* method:
```delphi
procedure CalcHashes(const FileName: string);
const
  BufSize = 16 * 1024;
 
var
  MD5, SHA1: THash;
  Stream: TStream;
  Buffer: array[0 .. BufSize - 1] of Byte;
  N: Integer;
 
begin
  MD5:= THash.MD5;
  SHA1:= THash.SHA1;
  try
    Stream:= TFileStream.Create(FileName,
                                fmOpenRead or fmShareDenyWrite);
    try
      repeat
        N:= Stream.Read(Buffer, BufSize);
        if N <= 0 then Break
        else begin
          MD5.Update(Buffer, N);
          SHA1.Update(Buffer, N);
        end;
      until False;
    finally
      Stream.Free;
    end;
    Writeln('MD5:  ', MD5.Digest.ToHex);
    Writeln('SHA1: ', SHA1.Digest.ToHex);
  finally
    MD5.Burn;
    SHA1.Burn;
  end;
end;
```
