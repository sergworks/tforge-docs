## [THash](../thash.md).Clone

Clones *THash* instance

---
### Syntax
```delphi
function THash.Clone: THash;
```

### Examples

*  compute *SHA256* digests of concatenated (file1, file2) and concatenated (file1, file3):
```delphi
procedure CalcDigests(const FileName1, FileName2, FileName3: string);
var
  Hash12, Hash13: THash;

begin
  Hash12:= THash.SHA256
               .UpdateFile(FileName1);
  Hash13:= Hash12.Clone();
  Writeln(Hash12.UpdateFile(FileName2).Digest.ToHex);
  Writeln(Hash13.UpdateFile(FileName3).Digest.ToHex);
end;
```
