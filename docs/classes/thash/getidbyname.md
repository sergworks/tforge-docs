## [THash](../thash.md).GetIDByName

Converts hash algorithm name to ID

---
### Syntax
```delphi
class function GetIDByName(const Name: string): TAlgID;
```

### Examples

```delphi
  Assert(THash.GetIDByName('md5') = ALG_MD5);
```
