## TCipher.Burn

Clears sensitive data stored in *TCipher* instance

---

### Syntax
```delphi
procedure TCipher.Burn;
```

### See also

* [TCipher.Free](free.md)

### Examples
```delphi
uses
  tfArrays, tfCiphers;

const
  HexKey = '000102030405060708090A0B0C0D0E0F';
  IV     = '0123456789ABCDEF0123456789ABCDEF';

var
  Cipher: TCipher;

begin
  Cipher:= TCipher.GetInstance(AES_CTR)
                  .Init(ByteArray.ParseHex(HexKey), ByteArray.ParseHex(IV));
  try
// print 22 bytes of the keystream
    Writeln(Cipher.KeyStream(22).ToHex);
  finally
// clear sensitive data stored in the instance
    Cipher.Burn;
  end;
end;
```
