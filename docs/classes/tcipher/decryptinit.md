## TCipher.DecryptInit

Initializes decryption operation

---

### Syntax
```delphi
function DecryptInit(AKey: PByte; AKeyLen: Cardinal): TCipher;
function DecryptInit(const AKey: ByteArray): TCipher;
function DecryptInit(AKey: PByte; AKeyLen: Cardinal; AIV: Pointer; AIVLen: Cardinal): TCipher;
function DecryptInit(const AKey: ByteArray; const AIV: ByteArray): TCipher;
function DecryptInit(AKey: PByte; AKeyLen: Cardinal; const ANonce: TNonce): TCipher;
function DecryptInit(const AKey: ByteArray; const ANonce: TNonce): TCipher;
```

### Parameters

*   *AKey* : Pointer to key, or _ByteArray_ containing key
*   *AKeyLen* : Length of key in bytes
*   *AIV* : Pointer to initialization vector, or _ByteArray_ containing initialization vector
*   *AIVLen* : Length of initialization vector in bytes
*   *Nonce* : Nonce

### Remarks

*   `TCipher.DecryptInit` method allows to reuse a _TCipher_ instance for decryption operation.

### See also

*   [TCipher.Init](init.md), [TCipher.EncryptInit](encryptinit.md)

