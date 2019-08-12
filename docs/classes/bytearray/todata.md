### Converts a *ByteArray* variable to integer type ###

## Syntax:
```
#!delphi
procedure ByteArray.ToInt(var Data; DataLen: Cardinal; Reversed: Boolean);
```

## Parameters:

*   *Data* - a buffer for output integer value 
*   *DataLen* - size of the *Data* buffer
*   *Reversed* - if *True* the byte order is reversed

##Remarks:

*   usually the byte order is reversed to change endianness, i.e. an integer type stores bytes in little-endian format, while *ByteArray* expects bytes in big-endian format 

## Exceptions:

*   *EByteArrayError* (code: *TF_E_INVALIDARG*) if the *ByteArray* data cannot be accommodated in an integer buffer of size *DataLen*

##See also:

*   [ByteArray.FromInt](FromInt)

## Example:
```
#!delphi
var
  A: ByteArray;
  L: LongWord;

begin
  A:= ByteArray.Parse('0 1 2 3');
  A.ToInt(L, SizeOf(L), False)
  Writeln(IntToHex(L, 8));      // '03020100'
  A.ToInt(L, SizeOf(L), True)
  Writeln(IntToHex(L, 8));      // '00010203'

  A:= ByteArray.Parse('0 1 2 3 4');
  A.ToInt(L, SizeOf(L), True)
  Writeln(IntToHex(L, 8));      // '01020304'
  A.ToInt(L, SizeOf(L), False)  // raises exception
  Writeln(IntToHex(L, 8));
end;
```