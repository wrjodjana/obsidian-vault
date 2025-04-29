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

**Asymmetric cipher:** pair of functions that can each both encrypt and decrypt, but only bounded-size inputs
- keys come in pair, for example $(f_1, f_2)$ is an asymmetric cipher and $(k_1, k_2)$ is a key pair
- property 1: $f_2(f_1(m, k_1),k_2) = m - k_2$ decrypts what $k_1$ encrypts
- property 2: $f_1(f_2(m,k_2), k_1)$ 


