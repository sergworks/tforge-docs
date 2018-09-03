## TCipher.Free

Decrements the reference count of a *TCipher* instance; if the reference count reaches zero, clears the sensitive information stored in the instance and frees memory occupied by the instance.

### Syntax:
```delphi
procedure TCipher.Free;
```

### Remarks:

*  There is little or no reason to call _TCipher.Free_ method manually; memory is freed automatically when all variables referencing an instance go out of scope.

## Example:
```delphi
uses
  tfCiphers;

// demonstrates what Free and IsAssigned methods are doing
var
  Cipher: TCipher;

begin
  Writeln(Cipher.IsAssigned);     // False
  Cipher:= TCipher.GetInstance('AES_CTR');
  Writeln(Cipher.IsAssigned);     // True
  Cipher.Free;
  Writeln(Cipher.IsAssigned);     // False
end;
```
