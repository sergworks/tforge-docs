### Decrements the reference count for a *ByteArray* instance

## Syntax:
```
#!delphi
procedure ByteArray.Free;
```

## Remarks:

*   a *ByteArray* instance is freed from memory when the reference count reaches zero.
*   there is no need to call `ByteArray.Free` explicitly; the instance is freed automatically when it goes out of scope
*   `ByteArray.Free` does **not** invoke `ByteArray.Burn` when the instance is freed from memory

## Example:
```
#!delphi

var
  A: ByteArray;

begin
  A:= ByteArray.Parse('10, 20, 30, 40', ',');
  Writeln(A.ToString);  // outputs '255 20 30 40'
  A.Free;
  Writeln(A.IsAssigned);
```