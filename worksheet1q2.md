# Cryptography Worksheet 1 CPA (Chosen Plaintext Attack) Question 2 Walkthrough

Consider an encryption scheme that works as follows: The plaintext messages m have length 2n. The secret key k has length n. To encrypt, for each bit m $_{i}$, compute m $_{i}$ ⊕ k⌊i/2⌋. In
other words, XOR 1st two bits of m with the 1st bit of k, the 2nd two bits of m with the 2nd bit of k, etc.

This is not a perfectly-secure encryption scheme: show an attack.