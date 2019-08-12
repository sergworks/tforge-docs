## TCipher.GetAuthTag

Retrieves authentication tag after encryption

---

### Syntax
```delphi
procedure TCipher.GetAuthTag(Data: Pointer; TagSize: Cardinal); overload;
function TCipher.GetAuthTag(TagSize: Cardinal): ByteArray; overload;
```

### Parameters

*   *Data* : Pointer to retrieve authentication tag
*   *TagSize* : Size of authentication tag

### Returns

*   Authentication tag (2nd overload)

### Remarks

*   If _GetAuthTag_ method is used with non-authenticated encryption, exception is thrown.

### Examples
```delphi
uses
  tfArrays, tfCiphers;

function EncryptGCM(const FileName: string; const Key, IV: ByteArray): ByteArray;
var
  Cipher: TCipher;

begin
  Cipher:= TCipher.GetInstance(AES_ENCRYPT_GCM);
  try
    Result:= Cipher.Init(Key, IV)
                   .AddAuthData(ByteArray.FromText('Encrypted in GCM mode'))
                   .EncryptFile(FileName, FileName + '.aes_gcm')
                   .GetAuthTag(16);
  finally
    Cipher.Burn;
  end;
end;
```

