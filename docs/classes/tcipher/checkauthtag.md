## TCipher.CheckAuthTag

Validates authentication tag after decryption

---

### Syntax
```delphi
function TCipher.CheckAuthTag(Data: Pointer; TagSize: Cardinal): Boolean; overload;
function TCipher.CheckAuthTag(const Tag: ByteArray): Boolean; overload;
```

### Parameters

*   *Data* : Pointer to authentication tag
*   *TagSize* : Size of authentication tag
*   *Tag* : Authentication Tag

### Returns

*   *True*  If authentication tag is valid
*   *False* If authentication tag is invalid

### Remarks

*   If _CheckAuthTag_ method is used with non-authenticated decryption, exception is thrown.

### Examples
```delphi
uses
  tfArrays, tfCiphers;

function DecryptGCM(const FileName: string; const Key, IV, Tag: ByteArray): Boolean;
var
  Cipher: TCipher;

begin
  Cipher:= TCipher.GetInstance(AES_DECRYPT_GCM);
  try
    Result:= Cipher.Init(Key, IV)
                   .AddAuthData(ByteArray.FromText('Encrypted in GCM mode'))
                   .DecryptFile(FileName + '.aes_gcm', FileName);
                   .CheckAuthTag(Tag);
    if not Result then begin
      Writeln('Authentication Failed!');
      DeleteFile(FileName);
    end;
  finally
    Cipher.Burn;
  end;
end;
```

