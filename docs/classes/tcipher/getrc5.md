## TCipher.GetRC5

Creates new _TCipher_ instance implementing customized *RC5* algorithm

---

### Syntax
```delphi
class function TCipher.GetRC5(AAlgID: TAlgID; BlockSize, Rounds: Cardinal): TCipher; static;
```
### Remarks

*   _TCipher.GetRC5_ method is supported by built-in engine only
*   *RC5* is a block cipher
*   *RC5* block size is 4, 8 or 16 bytes (32, 64 or 128 bits)
*   *RC5* key length is 0..255 *RC5 words*
*   *RC5 word* is:
    +    2 bytes for 4-byte block size 
    +    4 bytes for 8-byte block size 
    +    8 bytes for 16-byte block size
*   *RC5* number of rounds is 1..255
*   Standard *RC5* implementation created by [TCipher.GetInstance](getinstance.md) method has 8-byte block size and 12 rounds.

### Examples

Encrypt file with RC5 algorithm having 128-bit block size and 20 rounds in CBC mode of operation:
```delphi
uses
  tfArrays, tfCiphers;

procedure EncryptCBC(const FileName: string; const Key, IV: ByteArray);
var
  Cipher: TCipher;

begin
  Cipher:= TCipher.GetRC5(CBC_ENCRYPT, 16, 20);
  try
    Cipher.Init(Key, IV)
          .EncryptFile(FileName, FileName + '.rc5');
  finally
    Cipher.Burn;
  end;
end;
```

