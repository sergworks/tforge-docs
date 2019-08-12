## TCipher.Free

Clears sensitive data stored in _TCipher_ instance and dereferences _TCipher_ variable.

---

### Syntax
```delphi
procedure TCipher.Free;
```

### Remarks

*   Dereferencing does not necessarily deallocate memory of _TCipher_ instance; the memory is deallocated when the instance's reference count reaches zero, and it may happen later.
*   There is little practical difference between _TCipher.Free_ and _TCipher.Burn_ methods.

### See also

*   [TCipher.Burn](burn.md)

### Examples
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
