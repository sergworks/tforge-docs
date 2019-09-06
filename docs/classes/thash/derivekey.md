## [THash](../thash.md).DeriveKey

Derives key from user password using PBKDF1 (Password Based Key Derivation Function) algorithm

---
### Syntax
```delphi
function THash.DeriveKey(const Password, Salt: ByteArray; Rounds, dkLen: Integer): ByteArray;
```
### Remarks

*   PBKDF1 calculates the hash digest of *Password* concatenated with *Salt*, and then repeatedly calculates the hash digest of the digest returned by the previous step: H(H(...H(P||S)...))
*   if desired key length *dkLen* is greater than the hash digest size, exception is raised.

### Examples

*   Derive 16-byte key using 10000 rounds of *SHA1*:
```delphi
procedure DeriveKey(const Password, Salt: ByteArray);
begin
  Writeln('PBKDF1 Key: ',
    THash.SHA1.DeriveKey(Password, Salt,
                         10000,   // number of rounds
                         16       // key length in bytes
                         ).ToHex);
end;
```
