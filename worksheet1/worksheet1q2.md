# Cryptography Worksheet 1 CPA (Chosen Plaintext Attack) Question 2

Consider an encryption scheme that works as follows: The plaintext messages m have length 2n. The secret key k has length n. To encrypt, for each bit m $_{i}$, compute m $_{i}$ ⊕ k⌊i/2⌋. In
other words, XOR 1st two bits of m with the 1st bit of k, the 2nd two bits of m with the 2nd bit of k, etc.

This is not a perfectly-secure encryption scheme: show an attack.

## Solution
So the first bit of k could either be 0 or 1.
two messages:
01
If 0|k, 01 would be 01
If 1|k, 01 turn out to be 10

00
If 0|k, turns out to be 00
If 1|k, turns out to be 11
messages:
m0 -> 01 || random bits
m1 -> 00 || random bits

if the first bit is 01 or 10, m0, otherwise 00.