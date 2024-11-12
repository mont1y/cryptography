# Cryptography Worksheet 1 CPA (Chosen Plaintext Attack) Question 3

The following “encryption scheme” is not secure. Let k be a n bit key. To encrypt
an n-bit plaintext m, output ciphertext c = k ⊕ m. We use the same key k to encrypt every n-bit
plaintext message. (The symbol ⊕ is the bitwise XOR; recall that a ⊕ a ⊕ b = b.)

## Solution

uses the same key.
m0 -> 1 || random bits
c[0] = 0 if k[0] = 1 else 1
Ok from here we know what is the first bit of the key k.

Keep doing this for n times and then I will fully recorver the key.

As the distinguish:
m0 -> 10 || random bits
c[0] = 0 if k[0] = 1 else 1
c[1] = 0 if k[1] = 0 else 1
k could be:
10
01
11
00

c could be:
00
11
01
10

m1 -> 01 || random bits
c[0] 