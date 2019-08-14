## TCRC.Init

Initializes *TCRC* instance with a given CRC algorithm

### Syntax
```delphi
class function TCRC.Init(ABitSize: Cardinal; AGenerator: UInt64;
                      AXorIn, AXorOut: UInt64; ARevIn, ARevOut: Boolean): TCRC;
class function TCRC.Init(ABitSize: Cardinal; AGenerator: UInt64;
                      AXorIn, AXorOut: UInt64; ARevIn, ARevOut: Boolean;
                      ARevGen: Boolean): TCRC;
```

### Parameters

*   *ABitSize*: size of the shift register in bits, *1..64*
*   *AGenerator*: generator polynomial
*   *AXorIn*: initial state of the shift register
*   *AXorOut*: value to be *xor*'ed to the final shift register value before output
*   *ARevIn*: if *True* input bytes are fed into the shift register LSB first, otherwise MSB first
*   *ARevOut*: if *True* output digest is bit-reversed, otherwise normal
*   *ARevGen* if *True* the *AGenerator* parameter is in bit-reversed form, otherwise normal

### Remarks

*   if *ARevGen* parameter is omitted, the *AGenerator* parameter is in normal form

### Example
```delphi
var
  CRC32: TCRC;

// shows how initialize TCRC instance by standard CRC32 algorithm:
begin
  CRC32:= TCRC.Init(32, $04C11DB7, $FFFFFFFF, $FFFFFFFF, True, True);
// or simply
  CRC32:= TCRC.CRC32;
```
