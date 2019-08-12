## TCipher.DecryptFile

Decrypts a file

---

### Syntax
```delphi
function TCipher.DecryptFile(const InName, OutName: string): TCipher;
function TCipher.DecryptFile(const InName, OutName: string; BufSize: Cardinal): TCipher;
```

### Parameters

*   *InName* : Name of input (encrypted) file
*   *OutName* : Name of output (decrypted) file
*   *BufSize* : Size of intermediate buffer used for decryption

### Examples

```delphi
uses
  tfTypes, tfArrays, tfCiphers;

const
  Nonce = 42;

var
  FileName: string;
  Key: ByteArray;

begin
  FileName:= ParamStr(0);

// generate random key
  Key:= ByteArray.AllocateRand(16);
  Writeln('Key: ', Key.ToHex);

// encryption
  TCipher.GetInstance(AES_CBC_ENCRYPT).Init(Key, Nonce)
         .EncryptFile(FileName, FileName + 'Encrypted.aes');

// decryption
  TCipher.GetInstance(AES_CBC_DECRYPT).Init(Key, Nonce)
         .DecryptFile(FileName + 'Encrypted.aes', FileName + 'Decrypted.aes');

end;
```
