## TCRC

Implements CRC algorithms; declared in _tfCRCs_ unit.

---

### Class Methods
| Method       | Description   |
|--------------|---------------|
[Init](tcrc/init.md)               | Initializes *TCRC* instance
[BitReverse](tcrc/bitreverse.md)   | Reverses bit order
[CRC16](tcrc/crc16.md)             | Initializes *TCRC* instance as *CRC16*
[CRC32](tcrc/crc32.md)             | Initializes *TCRC* instance as *CRC32*

### Instance Methods
| Method       | Description   |
|--------------|---------------|
[Reset](tcrc/reset.md)         | Resets state of the shift register
[Update](tcrc/update.md)       | Updates state of the shift register after processing input data
[Digest](tcrc/digest.md)       | Returns final CRC digest and resets the shift register
[Hash](tcrc/hash.md)           | Processes input data, returns final CRC digest and resets the shift register 

### Properties
| Property     | Description   |
|--------------|---------------|
[BitSize](tcrc/bitsize.md)     | Number of bits in CRC digest
[Generator](tcrc/generator.md) | Generator polynomial in bit-reversed form

### Remarks

*   *TCRC* can implement any CRC algorithm of size up to 64 bits;
*   *TCRC* implements *Rocksoft™ Model* of CRC algorithms;
*   The list of known CRC algorithms can be found in [CRC RevEng Catalogue](http://reveng.sourceforge.net/crc-catalogue/)
