### Creates a new *ByteArray* instance and initializes it by integer bytes ###

## Syntax:
```
#!delphi
class function ByteArray.FromInt(const Data; DataLen: Cardinal; Reversed: Boolean): ByteArray;
```

##Parameters:

*   *Data*: buffer for initializing a new *ByteArray* instance
*   *DataLen*: size of the buffer (also length of a new *ByteArray* instance)
*   *Reversed*: if *True* then the byte order is reversed

##Remarks:

*   usually the byte order is reversed to change endianness, i.e. an integer type stores bytes in the little-endian format, while *ByteArray* expects bytes in the big-endian format. 
*   the method does not truncate leading zero bytes of the input *Data* and may be used with any data (not necessarily integer types) as well.

##See also:

*   [ByteArray.ToInt](ToInt)

##Example:
```
#!delphi
var
  A: ByteArray;
  I: LongWord;

begin
  I:= $030201;
  A:= ByteArray.FromInt(I, SizeOf(I), False);
  Writeln(A.ToString);    // '1 2 3 0'
  A:= ByteArray.FromInt(I, SizeOf(I), True);
  Writeln(A.ToString);    // '0 3 2 1'
```