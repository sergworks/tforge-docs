## THMAC

Implements HMAC (hashed message authentication code) algorithm; declared in _tfHashes_ unit

---
### Class Methods
| Method       | Description   |
|--------------|---------------|
[MD5](thmac/md5.md)          | Creates *THMAC* instance implementing *HMAC-MD5* algorithm
[SHA1](thmac/sha1.md)        | Creates *THMAC* instance implementing *HMAC-SHA1* algorithm
[SHA224](thmac/sha224.md)    | Creates *THash* instance implementing *HMAC-SHA224* algorithm
[SHA256](thmac/sha256.md)    | Creates *THash* instance implementing *HMAC-SHA256* algorithm
[SHA384](thmac/sha384.md)    | Creates *THash* instance implementing *HMAC-SHA384* algorithm
[SHA512](thmac/sha512.md)    | Creates *THash* instance implementing *HMAC-SHA512* algorithm
[GetInstance](thmac/getinstance.md) | Creates *THMAC* instance

### Instance Methods
| Method       | Description   |
|--------------|---------------|
[Burn](thmac/burn.md)          | Erases data stored in *THMAC* instance
[Clone](thmac/clone.md)        | Clones *THMAC* instance
[DeriveKey](thmac/derivekey.md)| Derives key from password using PBKDF2 algorithm
[Digest](thmac/digest.md) | Returns a message authentication code
[DigestSize](thmac/digestsize.md)   | Returns size of message authentication code
[DoneInstance](thmac/doneinstance.md)     | Outputs a message authentication code
[Free](thmac/free.md)     | Uninstantiates *THMAC* variable
[GetDigest](thmac/getdigest.md)     | Outputs a message authentication code
[Init](thmac/init.md)     | Initializes a *THMAC* instance state
[InitInstance](thmac/initinstance.md)     | Initializes a *THMAC* instance state
[IsAssigned](thmac/isassigned.md)   | Checks if *THMAC* variable is instantiated
[Update](thmac/update.md)         | Processes data and updates *THMAC* instance state
[UpdateInstance](thmac/updateinstance.md)         | Processes data and updates *THMAC* instance state
[UpdateFile](thmac/updatefile.md) | Processes file and updates *THMAC* instance state
[UpdateStream](thmac/updatestream.md) | Processes stream and updates *THMAC* instance state

