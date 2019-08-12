## TCipher.AddAuthData

Adds additional authentication data before encryption or decryption

---

### Syntax
```delphi
procedure TCipher.AddAuthData(Data: Pointer; DataSize: Cardinal); overload;
procedure TCipher.AddAuthData(const Data: ByteArray); overload;
```

### Parameters

*   *Data* : Pointer to authentication data, or _ByteArray_ containing authentication data
*   *DataSize* : Size of authentication data

### Remarks

*   If _AddAuthData_ method is used with non-authenticated encryption or decryption, exception is thrown.

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

