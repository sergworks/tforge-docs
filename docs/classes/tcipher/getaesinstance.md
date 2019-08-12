## TCipher.GetAESInstance

Creates new *TCipher* instance implementing *AES* algorithm

---

### Syntax

```delphi
class function TCipher.GetAESInstance(AAlgID: TAlgID): TCipher; static;
```

### Parameters

*   *AAlgID* : specifies backend engine, operation (encryption or decryption), mode of operation and padding

### Returns

*   TCipher instance implementing *AES* algorithm

### Remarks

*   *AES* is a block cipher
*   *AES* key length is 16, 24 or 32 bytes (128, 192 or 256 bits)
*   *AES* block size is 16 bytes (128 bits)

*   _GetAESInstance_ method is introduced to support smart linking. If you need AES algorithm only and don't want other algorithms in the executable file, use _GetAESInstance_ instead of _GetInstance_.

### See also

*   [GetInstance](getinstance.md)

### Examples

*   encrypt file using built-in engine, *CBC* mode of operation, *PKCS* padding:

```delphi
procedure EncryptCBC(const FileName: string; const Key, IV: ByteArray);
var
  Cipher: TCipher;

begin
  Cipher:= TCipher.GetAESInstance(ENCRYPT_CBC);
  try
    Cipher.Init(Key, IV)
          .EncryptFile(FileName, FileName + '.aes');
  finally
    Cipher.Burn;
  end;
end;
```

