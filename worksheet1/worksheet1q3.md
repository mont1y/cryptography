# Cryptography Worksheet 1 CPA (Chosen Plaintext Attack) Question 3

The following “encryption scheme” is not secure. Let k be a n bit key. To encrypt
an n-bit plaintext m, output ciphertext c = k ⊕ m. We use the same key k to encrypt every n-bit
plaintext message. (The symbol ⊕ is the bitwise XOR; recall that a ⊕ a ⊕ b = b.)

## Solution

c - ciphertext
m - message
k - secret key

to get the original message, just have the encryption scheme work twice
Dec(k, c) = k ⊕ c = k ⊕ (m ⊕ k) = (k ⊕ k) ⊕ m = m

to prove that the encryption scheme is not secure, we have it encrypt a message M.

m0 = M but first bit is flipped
m1 = random message that is not m0 nor M

send them to the encryption scheme, if the ciphertext has the same first bit as M, m0 was encrypted, otherwise m1.

Therefore the encryption scheme is not secure