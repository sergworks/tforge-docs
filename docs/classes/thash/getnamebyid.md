## [THash](../thash.md).GetNameByID

Converts hash algorithm ID to name

---
### Syntax
```delphi
class function GetNameByID(AlgID: TAlgID): string;
```

### Examples

```delphi
  Writeln(THash.GetNameByID(ALG_MD5));      // "MD5"
```
