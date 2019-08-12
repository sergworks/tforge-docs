## TCipher.DecryptByteArray

Decrypts data stored in *ByteArray*

---

### Syntax
```delphi
function TCipher.DecryptByteArray(const Data: ByteArray): ByteArray;
```

### Parameters

*   *Data* : _ByteArray_ containing encrypted data

### Returns

*   _ByteArray_ containing decrypted data

### Examples

```delphi
uses
  tfTypes, tfArrays, tfCiphers;

const
  Nonce = 42;

var
  Key: ByteArray;
  PlainText, DecryptedText: ByteArray;
  CipherText: ByteArray;

begin
// generate 16-byte AES key
  Key:= ByteArray.AllocateRand(16);

// generate 20-byte plaintext
  PlainText:= ByteArray.AllocateRand(20);

// encrypt plaintext
  CipherText:= TCipher.GetInstance(AES_ENCRYPT_CBC).Init(Key, Nonce)
                      .EncryptByteArray(PlainText);

// decrypt ciphertext
  DecryptedText:= TCipher.GetInstance(AES_DECRYPT_CBC).Init(Key, Nonce)
                         .DecryptByteArray(CipherText);

// Check encryption/decryption is correct:
  Assert(PlainText = DecryptedText);
end;
```
