## [THash](../thash.md).InitInstance

Initializes *THash* instance state

---
### Syntax
```delphi
procedure THash.InitInstance;
```

### Remarks
*   In most cases there is no need to call *THash.InitInstance*; when a new *THash* instance is created, ex `SHA256:= THash.SHA256`, the instance state is already initialized; the instance state is also (re)initialized after computing final digest, ex:

```delphi
var
  SHA256: THash;
  Digest: ByteArray;

begin
  SHA256:= THash.SHA256;
  SHA256.Update(Data, DataSize);
  Digest:= SHA256.Digest;
// SHA256 instance state is properly initialized here
  ..
end;
```

*   probably the only case when you should call *THash.Init* is cancelling hashing without computing final digest, ex:

```delphi
var
  SHA256: THash;
  Digest: ByteArray;

begin
  SHA256:= THash.SHA256;
  SHA256.Update(Data, DataSize);
// for some reason we don't want to continue with obtaining the final digest,
//   so we initialize SHA256 instance to reuse it:
  SHA256.InitInstance;
  SHA256.Update(OtherData, OtherDataSize);
  Digest:= SHA256.Digest;
end;
```

*   *THash.InitInstance*, *THash.UpdateInstance* and *THash.DoneInstance* methods constitute traditional (non-fluent) hash-computing API.

