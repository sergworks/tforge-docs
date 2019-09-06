## TMont

Implements Montgomery modular arithmetic; declared in _tfNumerics_ unit.

---

### Class Methods
| Method       | Description   |
|--------------|---------------|
[GetInstance](tmont/getinstance.md) | Creates new *TMont* instance

### Instance Methods
| Method       | Description   |
|--------------|---------------|
[Free](tmont/free.md)             | Uninstantiates *TMont* variable
[IsAssigned](tmont/isassigned.md) | Checks if *TMont* variable is instantiated
[Burn](tmont/burn.md)             | Destroys data stored in *TMont* instance
[Convert](tmont/convert.md)       | Converts a number into Montgomery form
[Reduce](tmont/reduce.md)         | Converts a number out of Montgomery form
[Add](tmont/add.md)               | Modular addition
[Subtract](tmont/subtract.md)     | Modular subtraction
[Multiply](tmont.multiply.md)     | Montgomery multiplication
[ModMul](tmont/modmul.md)         | Modular multiplication 
[ModPow](tmont/modpow)            | Modular exponentiation 
[GetRModulus](tmont/getrmodulus.md) | Returns auxiliary modulus


### Remarks

*   In many applications of modular arithmetic the modulus is fixed; Montgomery arithmetic precomputes some numeric data for a given modulus to make modular multiplication faster. The most notable application of Montgomery arithmetic is modular exponentiation; Montgomery modular exponentiation is the fastest general modular exponentiation algorithm.
