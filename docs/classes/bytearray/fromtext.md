## ByteArray.FromText

Creates new *ByteArray* instance and initializes it by string bytes

---

### Syntax
```delphi
class function ByteArray.FromText(const S: string): ByteArray;
```

### Parameters

*   *S*: string used for initializing a new *ByteArray* instance

### Remarks

*   the string *S* is converted to *UTF8* format and then used 'as is', without parsing; ex the latin 'a' character in the string becomes the byte *97 ($61)* in the ByteArray. 

### See also
*   [ByteArray.ToText](totext)

### Example
```delphi
var
  A: ByteArray;

begin
  A:= ByteArray.FromText('Hello, World!');
  Writeln(A.ToString);  // '72 101 108 108 111 44 32 87 111 114 108 100 33'
  Writeln(A.ToText);    // 'Hello, World!'
end;
```
