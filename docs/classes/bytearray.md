## ByteArray

Implements array of bytes; declared in _tfArrays_ unit.

---
### Class Methods
| Method       | Description   |
|--------------|---------------|
[AddBytes](bytearray/addbytes.md)             | Bytewise (modulo 256) addition of *ByteArray* operands
[Alloc](bytearray/alloc.md)                   | Creates a new *ByteArray* instance of a given length
[Concat (**+**)](bytearray/concat.md)         | Concatenates *ByteArray* instances
[Copy](bytearray/copy.md)                     | Copies *ByteArray* instance
[Decr](bytearray/decr.md)                     | Decrements integer value stored in a *ByteArray* instance
[Fill](bytearray/fill.md)                     | Fills the bytes of a *ByteArray* instance by a given value
[FromData](bytearray/fromdata.md)             | Creates a new *ByteArray* instance from integer value
[FromText](bytearray/fromtext.md)             | Creates a new *ByteArray* instance from string bytes
[Incr](bytearray/incr.md)                     | Increments integer value stored in a *ByteArray* instance
[Insert](bytearray/insert.md)                 | Inserts bytes into a *ByteArray* instance
[Parse](bytearray/parse.md)                   | Creates new *ByteArray* instance from parsed string
[ParseHex](bytearray/parsehex.md)             | Creates new *ByteArray* instance from parsed hexadecimal string
[Realloc](bytearray/realloc.md)               | Reallocates *ByteArray* instance in memory
[Remove](bytearray/remove.md)                 | Removes bytes from *ByteArray*
[SubBytes](bytearray/subbytes.md)             | Bytewise (modulo 256) subtraction of *ByteArray* instances
[TryParseHex](bytearray/tryparsehex.md)       | Creates new *ByteArray* instance from parsed hexadecimal string

### Instance Methods
| Method       | Description   |
|--------------|---------------|
[Burn](bytearray/burn.md)             | Clears data stored in *ByteArray* instance
[Clone](bytearray/clone.md)           | Clones *ByteArray* instance
[Delete](bytearray/delete.md)         | Deletes bytes from *ByteArray* instance
[Free](bytearray/free.md)             | Dereferences *ByteArray* variable
[IsAssigned](bytearray/isassigned.md) | Checks if *ByteArray* variable is instantiated
[Reverse](bytearray/reverse.md)       | Reverses byte order in a *ByteArray*
[ToData](bytearray/todata.md)         | Converts *ByteArray* variable to integer type
[ToText](bytearray/totext.md)         | Converts *ByteArray* variable to text string
[HashCode](bytearray/hashcode.md)     | Returns 32-bit hash value for *ByteArray* instance
[Raw](bytearray/raw.md)               | Returns pointer to bytes stored in a *ByteArray* instance

### Properties
|Property      | Description   |
|--------------|---------------|
[Len](bytearray/len.md)              | Number of bytes in a *ByteArray* instance

---

### Operators

*ByteArray* class supports the following operators:

*   Binary bit logic operators: `and`, `or`, `xor` (operands must have equal length)
*   Unary bit logic operator: `not`
*   Bitwise shift operators: `shl`, `shr`
*   Plus `+` operator implements [Concat](bytearray/concat.md) class method

---

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
    end;
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
    end;
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
    end;
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
    end;
```

---
