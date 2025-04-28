### Hashes

**Hash function:** takes an input of any size and returns output of a fixed size (large binary number)
- deterministic, un-reversible, collision resistant
- password-hashes: abcd -> aslj3456789a
- password vulnerabilities: using a salt further separates the hash by one more step

### Ciphers

**Symmetric cipher:** pair of functions, one to encrypt and one to decrypt
- takes two inputs: message of arbitrary length and limited-size secret key
- property 1: $e(m,k) = c \neq m$ (encryption results in a ciphertext which is unlike the original message)
- property 2: $d(e(m,k),k) = m$ (decryption undoes encryption)
- recovering $m$ from $e$ and $c$ without $k$ is no easier than trying every possible $k$ until one works

**Asymmetric cipher:** 


