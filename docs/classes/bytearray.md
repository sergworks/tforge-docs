## ByteArray

Implements array of bytes; declared in _tfArrays_ unit.

---
### Class Methods
| Method       | Description   |
|--------------|---------------|
[AddBytes](bytearray/addbytes.md)             | Byte-wise (modulo 256) addition of *ByteArray* instances
[AndBytes (**and**)](bytearray/andbytes.md)   | Bit-wise **and** of *ByteArray* operands
[Alloc](bytearray/alloc.md)                   | Creates a new *ByteArray* instance of a given length
[Concat (**+**)](bytearray/concat.md)         | Concatenates *ByteArray* instances
[FromData](bytearray/fromdata.md)             | Creates a new *ByteArray* instance from integer value
[FromText](bytearray/fromtext.md)             | Creates a new *ByteArray* instance from string bytes
[OrBytes (**or**)](bytearray/orbytes.md)      | Bit-wise **or** of *ByteArray* operands
[Parse](bytearray/parse.md)                   | Creates a new *ByteArray* instance from parsed string
[ParseHex](bytearray/parsehex.md)             | Creates a new *ByteArray* instance from parsed hexadecimal string
[SubBytes](bytearray/subbytes.md)             | Byte-wise (modulo 256) subtraction of *ByteArray* instances
[TryParseHex](bytearray/tryparsehex.md)       | Creates a new *ByteArray* instance from parsed hexadecimal string
[XorBytes (**xor**)](bytearray/xorbytes.md)   | Bit-wise **xor** of *ByteArray* operands

---
### Instance Methods
| Method       | Description   |
|--------------|---------------|
[Burn](Burn)             | Clears data stored in *ByteArray* instance
[Copy](Copy)             | Duplicates a *ByteArray* instance
[Decr](Decr)             | Decrements integer value stored in a *ByteArray* instance
[Fill](Fill)             | Fills the bytes of a *ByteArray* instance by a given value
[Free](Free)             | Decrements the reference count for a *ByteArray* instance
[Incr](Incr)             | Increments integer value stored in a *ByteArray* instance
[Insert](Insert)         | Inserts bytes into a *ByteArray*
[IsAssigned](IsAssigned) | Checks if a *ByteArray* variable is instantiated
[Realloc](Realloc) | Reallocates a *ByteArray* instance in memory
[Remove](Remove)         | Removes bytes from a *ByteArray*
[Reverse](Reverse)       | Reverses byte order in a *ByteArray*
[ToInt](ToInt)           | Converts a *ByteArray* variable to integer type
[ToText](ToText)         | Converts a *ByteArray* variable to text string
[HashCode](HashCode)    | 32-bit hash value for a *ByteArray* bytes
[Raw](Raw)      | Pointer to bytes stored in a *ByteArray* instance

|Property      | Description   |
|--------------|---------------|
[Len](Len)              | Number of bytes in a *ByteArray*

### Remarks

*ByteArray* class was originally desined for storing cryptography data such as secret keys, initialization vectors, etc.
The data is automatically destroyed (zeroed) when variable(s) referencing *ByteArray* instance go out of scope.

*   *ByteArray* is a dynamically allocated array of bytes of variable length;
*   *ByteArray* is a lifetime-managed type; there is no need to free a *ByteArray* instance explicitly;

*ByteArray* supports standard methods of accessing the array's elements:

* indexed access with range check:

```nohighlight
    var
      A: ByteArray;
      I: Cardinal;

    begin
      A:= ByteArray.Alloc(4);
      for I:= 0 to A.Len - 1 do begin
        A[I]:= I + 1;
        Write(A[I]:2);   // outputs '1 2 3 4'
      end;
      Writeln;
      Writeln(A[A.Len]); // raises  EArgumentOutOfRangeException
```

* faster indexed access without range check:

```nohighlight
    var
      A: ByteArray;
      I: Cardinal;

    begin
      A:= ByteArray.Alloc(4);
      for I:= 0 to A.Len - 1 do begin
        A.Raw[I]:= I + 1;
        Write(A.Raw[I]:2);   // outputs '1 2 3 4'
      end;
      Writeln;
    //  Writeln(A.RawData[A.Len]); never do it because the range error is not caught!
```

* pointer access:

```nohighlight
    var
      A: ByteArray;
      P, Sentinel: PByte;

    begin
      A:= ByteArray.Alloc(4);
      P:= A.Raw;
      Sentinel:= P + A.Len;
      while P <> Sentinel do begin
        P^:= 42;
        Write(P^:3);  // outputs '42 42 42 42'
        Inc(P);
      end;
      Writeln;
```

* `for .. in` enumeration:

```nohighlight
    var
      A: ByteArray;
      B: Byte;

    begin
      A:= ByteArray.Parse('1 2 3 4');
      for B in A do
        Write(B:2);   // outputs '1 2 3 4'
      Writeln;
```

---
