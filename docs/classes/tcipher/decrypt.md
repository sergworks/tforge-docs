## TCipher.Decrypt

Processing a data part in a multi-part decryption operation

---

### Syntax
```delphi
procedure TCipher.Decrypt(Data, OutData: Pointer; DataSize: Cardinal);
```

### Parameters

*   *Data* : Pointer to data to be decrypted
*   *OutData* : Pointer to buffer to receive decrypted data
*   *DataSize* : Size of data

### Remarks

*   `TCipher.Decrypt` method assumes that size of decrypted data is the same as size of source (encrypted) data; the assumption is not true if encryption uses padding. To decrypt data encrypted with padding use `TCipher.DecryptUpdate` method.

### See also

*   [TCipher.DecryptUpdate](decryptupdate.md)

