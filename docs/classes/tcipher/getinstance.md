## TCipher.GetInstance

Creates new *TCipher* instance

---

### Syntax
```delphi
class function TCipher.GetInstance(AAlgID: TAlgID): TCipher; static;
```

### Parameters

*   *AAlgID* : specifies backend engine, algorithm, operation (encryption or decryption), mode of operation and padding

### Returns

*   TCipher instance implementing algorithm specified by *AAlgID* parameter

### Remarks

*   Operation field is mutable; for example, you can create *TCipher* instance with encryption operation specified, use it for encryption by calling [Init](init.md) and later reuse the instance for decryption by calling [DecryptInit](decryptinit.md). Operation may not be defined in *AAlgID* and specified later by calling [EncryptInit](EncryptInit) for encryption or [DecryptInit](decryptinit.md) for decryption.

### Examples

Encrypt file using built-in engine, *AES* algorithm, *CBC* mode of operation, *PKCS* padding

```delphi
uses
  tfArrays, tfCiphers;

procedure EncryptCBC(const FileName: string; const Key, IV: ByteArray);
var
  Cipher: TCipher;

begin
  Cipher:= TCipher.GetInstance(AES_CBC_ENCRYPT);
  try
    Cipher.Init(Key, IV)
          .EncryptFile(FileName, FileName + '.aes');
  finally
    Cipher.Burn;
  end;
end;
```

