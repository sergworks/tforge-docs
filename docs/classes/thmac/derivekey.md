## [THMAC](../thmac.md).DeriveKey

Derives key from user password using PBKDF2 (Password Based Key Derivation Function) algorithm

---
### Syntax
```delphi
function THMAC.DeriveKey(const Password, Salt: ByteArray; Rounds, dkLen: Integer): ByteArray;
```

### Examples

*   Derive 20-byte key using 10000 rounds of *SHA1*:
```delphi
procedure DeriveKey(const Password, Salt: ByteArray);
begin
  Writeln('PBKDF2 Key: ',
    THMAC.SHA1.DeriveKey(Password, Salt,
                         10000,   // number of rounds
                         20       // key length in bytes
                         ).ToHex);
end;
```
