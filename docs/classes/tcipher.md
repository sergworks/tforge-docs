## TCipher

Implements secret-key encryption and decryption; declared in _tfCiphers_ unit.

---
### Class Methods
| Method       | Description   |
|--------------|---------------|
[GetInstance](tcipher/getinstance.md) | Creates *TCipher* instance implementing a given algorithm 
[GetRC5](tcipher/getrc5.md)           | Creates *TCipher* instance implementing customized *RC5* algorithm
[GetSalsa](tcipher/getsalsa.md)       | Creates *TCipher* instance implementing customized *Salsa* algorithm
[GetChaCha](tcipher/getchacha.md)     | Creates *TCipher* instance implementing customized *ChaCha* algorithm

---
### Instance Methods
| Method       | Description   |
|--------------|---------------|
[AddAuthData](tcipher/addauthdata.md)    | Adds additional authentication data before encryption or decryption
[Burn](tcipher/burn.md)                  | Clears sensitive data stored in *TCipher* instance
[Clone](tcipher/clone.md)                | Clones *TCipher* instance
[Decrypt](tcipher/decrypt.md)            | Decrypts memory data
[DecryptBlock](tcipher/decryptblock.md)  | Decrypts block of data
[DecryptByteArray](DecryptByteArray)  | Decrypts data stored in *ByteArray*
[DecryptStream](DecryptStream)| Decrypts a stream of data
[DecryptFile](DecryptFile)    | Decrypts a file
[Free](tcipher/free.md)                  | Uninstantiates *TCipher* variable
[Encrypt](Encrypt)            | Encrypts arbitrary memory data
[EncryptBlock](EncryptBlock)  | Encrypts a block of data
[EncryptByteArray](EncryptByteArray)  | Encrypts a *ByteArray*
[EncryptStream](EncryptStream)| Encrypts a stream of data
[EncryptFile](EncryptFile)    | Encrypts a file
[ExpandKey](ExpandKey)        | Expands a secret key into a form used by an algorithm
[IsAssigned](IsAssigned)      | Checks if a *TCipher* variable is instantiated
[Apply](Apply)                | Encrypts/decrypts arbitrary memory data by a keystream
[KeyStream](KeyStream)        | Generates a given number of keystream bytes
[SetIV](SetIV)                | Sets an IV value in a *TCipher* instance state
[SetNonce](SetNonce)          | Sets a nonce value in a *TCipher* instance state
[Skip](Skip)                  | Discards a given number of keystream blocks

---
### Backend engines

_TCipher_ is frontend class supported by two backend engines:

* Built-in engine implemented by _TForge_ itself;
* External OpenSSL engine implemented by _libcrypto_ (OpenSSL 1.1.0+) or _libeay32_ (OpenSSL 1.0.2) library.

Using external backend has its limitations: some _TCipher_ methods requiring access to the internal cipher instance structures can't be implemented by an external backend, and some algorithms are not supported by OpenSSL; _TCipher_ throws exception if you try to use them, but many methods and algorithms are supported by OpenSSL and in most cases it is enough.

To use OpenSSL backend you should:

* Load _libcrypto (libeay32)_ library by calling [LoadLibCrypto](../functions/loadlibcrypto.md) function;
* Set *ENGINE_OSSL* flag in *AAlgID* parameter of [TCipher.GetInstance](tcipher/getinstance.md) method's call.

For example to use built-in backend, _AES_ algorithm and _CTR_ mode of operation:
```nohighlight
    var
      Cipher: TCipher;

    begin
      Cipher:= TCipher.GetInstance(AES_CTR);
      ...
```
Using OpenSSL backend:
```nohighlight
    var
      Cipher: TCipher;

    begin
      Cipher:= TCipher.GetInstance(ENGINE_OSSL or AES_CTR);
      ...
```
That is all; now _Cipher_ methods are implemented by OpenSSL backend.

---
### Coding paradigms

_TCipher_ supports two coding paradigms:

* fluent coding;
* traditional coding.

Lets consider an example: encrypt file using *AES* algorithm in *GCM* mode of operation and obtain authentication tag:

-   fluent coding:
```nohighlight
    uses
      tfArrays, tfCiphers;

    function EncryptGCM(const FileName: string; const Key, IV: ByteArray): ByteArray;
    begin
      Result:= TCipher.GetInstance(AES_GCM_ENCRYPT)
                      .Init(Key, IV)
                      .AddAuthData(ByteArray.FromText('Encrypted in GCM mode'))
                      .EncryptFile(FileName, FileName + '.aes_gcm')
                      .GetAuthTag(16);
    end;
```
-   traditional coding:
```nohighlight
    uses
      tfArrays, tfCiphers;

    function EncryptGCM(const FileName: string; const Key, IV: ByteArray): ByteArray;
    var
      Cipher: TCipher;

    begin
      Cipher:= TCipher.GetInstance(AES_GCM_ENCRYPT);
      try
        Cipher.Init(Key, IV);
        Cipher.AddAuthData(ByteArray.FromText('Encrypted in GCM mode'));
        Cipher.EncryptFile(FileName, FileName + '.aes_gcm');
        Result:= Cipher.GetAuthTag(16);
      finally
        Cipher.Burn;
//        Cipher.Free;
      end;
    end;
```

The fluent coding is outright gorgeous. _TCipher_ implements automatic memory management and there is no need to call [TCipher.Free](tcipher/free.md) method to deallocate memory used by _TCipher_ instance; fluent coding leverages automatic memory management.

[TCipher.Free](tcipher/free.md) method does not guaranty that the memory is freed: it decrements the instance's reference count and frees memory (having cleared the sensitive information first) if the reference count reaches zero; there is little or no reason to call [TCipher.Free](tcipher/free.md) manually.

The traditional coding has its pros too: the [TCipher.Burn](tcipher/burn.md) method called in `finally` section clears sensitive information stored in _Cipher_ instance.

You can take the best from both worlds, and the recommended code is:
```nohighlight
    uses
      tfArrays, tfCiphers;

    function EncryptGCM(const FileName: string; const Key, IV: ByteArray): ByteArray;
    var
      Cipher: TCipher;

    begin
      Cipher:= TCipher.GetInstance(AES_GCM_ENCRYPT);
      try
        Result:= Cipher.Init(Key, IV)
                       .AddAuthData(ByteArray.FromText('Encrypted in GCM mode'))
                       .EncryptFile(FileName, FileName + '.aes_gcm')
                       .GetAuthTag(16);
      finally
        Cipher.Burn;
      end;
    end;
```

---
### Modes of operation

Mode of operation is an algorithm that uses block cipher algorithm to encrypt and decrypt data of arbitrary length; a block cipher algorithm encrypts and decrypts blocks of fixed length (called cipher block size) only.

_TCipher_ supports the following modes of operation:

| Mode         | Description   |
|--------------|---------------|
ECB | Electronic Code Book
CBC | Cipher Block Chaining
CFB | Cipher Feedback
OFB | Output Feedback
CTR | Counter
GCM | Galois Counter Mode

_ECB_ mode of operation is deterministic (encryption with the same key always produces the same ciphertext from the same plaintext) and not recommended to use, other modes of operation are indeterministic (provided the initialization vectors are generated correctly).

_ECB_ and _CBC_ modes of operation encrypt plaintext by blocks (of cipher block size length) and require padding to encrypt plaintext of arbitrary length; other modes of operation encrypt plaintext by bytes and don't need padding.

_GCM_ is authenticated mode of operation and supported for 128-bit block ciphers only.

For detailed description of block cipher modes of operation see [Wikipedia](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation).

---
### Nonces

Nonce is "number used once". Nonce can be considered as non-secret part of a key. If you encrypt multiple messages, each message must be encrypted with a unique key, but not necessarily unique secret key. In many cases it is allowed to reuse secret key provided each message is encrypted with unique nonce, and nonce need not be kept secret. Nonces can be deterministic (generated by a counter or a LFSR) or random; deterministic nonces never repeat by design, for random nonces the probability of generating two identical nonces during the lifetime of a secret key must be negligible.

_TForge_ defines
```nohighlight
    type TNonce = UInt64;
```
and _TCipher_ supports 64-bit nonces for 128-bit block cipher algorithms and _Salsa_ and _ChaCha_ stream cipher algorithms in [Init](tcipher/init), [EncryptInit](tcipher/encryptinit) and [DecryptInit](tcipher/decryptinit) methods' overloads. _Salsa_ and _ChaCha_ support 64-bit nonces by design, for 128-bit block ciphers in _CBC_, _CFB_, _OFB_ and _CTR_ modes of operation nonce is implemented as the left half of 128-bit _IV_, and for 128-bit block ciphers in _GCM_ mode of operation nonce is bits [_32..95_] of 96-bit _IV_.

In many cases it is more convenient to use nonces than to use initialization vectors. Consider encryption of multiple messages with _AES_ block cipher algorithm in _CTR_ mode of operation with the same secret key. Let the first message is encrypted with zero initialization vector, and the message size is _10000_ bytes; _10000_ bytes are contained in _625=0x271_ 16-byte _AES_ blocks, and it is user responsibility not to reuse initialization vectors in the range from (hexadecimal)
```nohighlight
    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```
to
```nohighlight
    00 00 00 00 00 00 00 00 00 00 00 00 00 00 02 70
```
otherwise you end up with double-time pad and encryption is completely broken. Using nonces you can simply generate deterministic nonces by a counter or a LFSR, and there is no such problem; the only limitation here is that a message size should not exceed 2<sup>64</sup> blocks and the number of messages should not exceed 2<sup>64</sup>, but you should not encrypt more than 2<sup>64</sup> blocks with an ideal 128-bit block cipher using the same secret key by security considerations anyway. For _AES_ it is reasonable to change secret key after encrypting about 2<sup>40</sup> blocks or less.

---
### Paddings

*ECB* and *CBC* modes of operation require that the size of input data to be encrypted is multiple of the cipher block size. *Padding* extends plaintext so that the total size of the data to be encrypted is multiple of the cipher block size; when the ciphertext is decrypted, the padded block is decoded and the original plaintext size is restored.

*TCipher* supports padding for *ECB* and *CBC* modes of operation only; the other modes of operation supported by *TCipher* do not need padding and you should not specify padding for them.

The default padding is *PKCS*; if padding is not specified for *ECB* or *CBC* modes of operation, the *PKCS* padding applies. 

*PKCS* and *ISO* are the only types of padding defined in acting official standards; they must be implemented identically in all cryptography libraries. The *NONE* padding is also implemented identically because it can't be implemented otherwise. The other paddings are implementation dependent.

OpenSSL backend supports *NONE* and *PKCS* paddings only.

Padding is specified in [TCipher.GetInstance](tcipher/getinstance.md) method's call, for example
```nohighlight
    var
      Cipher: TCipher;

    begin
      Cipher:= TCipher.GetInstance(AES_CBC_ENCRYPT or PADDING_ISO);
      ...
```
The following types of padding are supported:

*   *NONE* : No padding applies. The plaintext size must be multiple of the cipher block size, otherwise encryption fails.  
*NONE* padding can be used to implement other types of padding manually.  
*NONE* padding is exact equivalent of the Java Bouncycastle *NoPadding*.

*   *ZERO* : The plaintext is extended, if needed, with zero bytes *0x00* until the size is multiple of the cipher block size. This is not recommended type of padding because the plaintext size can't be recovered during decryption.  
The decryption with *ZERO* padding specified is equivalent to decryption with *NONE* padding specified. The ciphertext size is greater than the plaintext size by *0* to *cipher block size - 1* bytes.  
*ZERO* padding is non-standard.  
Example (block size is 8 bytes, 4 padded bytes, hexadecimal):
```nohighlight
    ... | DD DD DD DD DD DD DD DD | DD DD DD DD 00 00 00 00 |
```

*   *ANSI* : The plaintext is extended, if needed, with zero bytes *0x00* until the size is one byte less the multiple of the cipher block size, and then mandatory byte containing the number of padded bytes is added.  
If the plaintext size is already multiple of the cipher block size, a new block is added (containing zero bytes and cipher block size byte). The ciphertext size is greater than the plaintext size by *1* to *cipher block size* bytes.  
The decryption with *ANSI* padding specified does not check the zero padded bytes; it only checks the last byte to recover the plaintext size. *ANSI* padding can be used to decrypt legacy types of padding that store the number of padded bytes as the last byte of the padded block.  
*ANSI* padding is non-standard.  
Example (block size is 8 bytes, 4 padded bytes, hexadecimal):
```nohighlight
    ... | DD DD DD DD DD DD DD DD | DD DD DD DD 00 00 00 04 |
```

*   *PKCS* : The plaintext is extended with bytes containing the number of padded bytes.  
If the plaintext size is already multiple of the cipher block size, a new block is added (all bytes are equal to block size). The ciphertext size is greater than the plaintext size by *1* to *cipher block size* bytes.  
The decryption with *PKCS* padding specified checks that all padded bytes are equal, otherwise decryption fails.  
*PKCS* padding is defined in [RFC 5652](https://tools.ietf.org/html/rfc5652#section-6.3).  
*PKCS* padding is exact equivalent of the Java Bouncycastle *PKCS7Padding*.  
Example (block size is 8 bytes, 4 padded bytes, hexadecimal):
```nohighlight
    ... | DD DD DD DD DD DD DD DD | DD DD DD DD 04 04 04 04 |
```

*   *ISO* : The plaintext is extended with one mandatory byte *0x80* and, if needed, zero bytes *0x00* until the size is multiple of the cipher block size.  
If the plaintext size is already multiple of the cipher block size, a new block is added (containing byte *0x80* and zero bytes). The ciphertext size is greater than the plaintext size by *1* to *cipher block size* bytes.  
*ISO* padding is defined in *ISO/IEC 7816-4* standard (6.2.3.1).  
*ISO* padding is exact equivalent of the Java Bouncycastle *ISO7816-4Padding*.  
Example (block size is 8 bytes, 4 padded bytes, hexadecimal):
```nohighlight
    ... | DD DD DD DD DD DD DD DD | DD DD DD DD 80 00 00 00 |
```

---
