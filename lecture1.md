# Cryptography Property

### Confidentiality 
Information is not disclosed to to unauthorized parties

### Integrity
Information is accurate and complete

"Information is unaltered from A to B"

### Authenticity
Information originated from its purported source

"Information claimed to be sent by A is actually from A"

# Encryption Scheme

The definition of an encryption scheme is made up of:

### Correctness
The encrypted message must be decryptable

### Security
The adversary cannot read the encrypted message without the secret key

---

### Notation:

The encryption scheme encrypts message m with secret key k:

**Enc $_{k}$ (m)**

The encryption scheme decrypts the encrypted message m with secret key k:

**Dec $_{k}$ (Enc $_{k}$ (m))**

# Kerckhoff's Principle / Shannon's Maximum

The principle describes "the enemy knows the system."

In other words, "one ought to design systems under the assumption that the enemy will immediately gain full familiarity with them."

# One Time Pad (OTP)

1. Generate a single-use seret key of the same length as the plaintext we want to encrypt.

2. XOR each bit in the plaintext with each bit in the secret key to get the ciphertext

3. The receiver can decrypt the ciphertext use the secret key


### Semantic Security Game for One-Time Pad (OTP)

1. The adversary generates two messages m $_{0}$ and m $_{1}$ and send it to the challenegr

2. The challenger randomly picks one of the messages: m $_{0}$ or m $_{1}$

3. The challenger encrypts the message
    1. Generate random key k. Length(k) = Length(m)
    2. Encrypts m by XOR each bit with k

4. The challenger sends the ciphertext to the adversary

5. Finally, the adversary has only 50/50 chance of guessing which message was encrypted by the challenger

With OTP, the adversary has a 50% chance of guessing which message was encrypted, the same as random guessing, meaning OTP is semantically secure.