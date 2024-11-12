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

An encryption scheme must have:

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

# Block Cipher
A block cipher is a way of encrypting data by breaking it into fixed-size chunks, called "blocks," and then scrambling each block using a secret key.

1. Divide the Message: The data (like a message) is split into equal-sized blocks, say 128 bits (16 bytes) each.
2. Encrypt Each Block: Each block is then encrypted separately using the same secret key, transforming it into a scrambled version.
3. Combine the Blocks: All the encrypted blocks are put back together to form the final encrypted message.

## Electronic Codebook (ECB) Mode - Insecure

ECB (Electronic Codebook) Mode is one of the simplest ways to use a block cipher to encrypt data.

1. Divide the Data into Blocks

2. Encrypt Each Block Separately

3. Concatenate Encrypted Blocks

ECB is simple but insecure for large or patterned data, because it doesn’t hide patterns.

# Secure - Cipher Block Chaining (CBC)

CBC (Cipher Block Chaining) is a mode of operation for block ciphers that enhances security by linking each block of plaintext with the previous ciphertext block.

1. Encryption starts with a random **Initialization Vector** (IV), which is a random block that adds randomness to the process and ensures that the same plaintext encrypted twice produces different ciphertexts.

2. The plaintext block is XORed with the previous ciphertext block (or the IV for the first block).

3.  The result of the XOR operation is then encrypted using the block cipher and secret key, producing the ciphertext for that block.
This process is repeated for each block, creating a "chain" effect.

Because each plaintext block is combined with the previous ciphertext, any change in one block will affect all subsequent blocks, making it harder for attackers to spot patterns.

CBC mode provides strong security against pattern detection by chaining blocks together.

# Stream Cipher

A stream cipher is an encryption method that encrypts data one bit or byte at a time, rather than in fixed-size blocks. It’s fast and ideal for situations where data arrives in a continuous stream, like network data or real-time applications.

1. Generate a Key Stream: Using a secret key, the stream cipher generates a long, pseudo-random sequence of bits (called the key stream). This key stream is as long as the data that needs to be encrypted.

2. Encrypt Data Bit by Bit: Each bit of the plaintext is XORed with a corresponding bit from the key stream (This process is reversed for decryption).

3. Continuous Process: Since it processes data bit by bit, stream ciphers are efficient for streaming data where the message length isn’t fixed.

Secure, High Speed, No Pattern Leakage,
Sensitive to Key Reuse.

# Threat Model

### Eavesdropper
Can only read the data

### Man-in-the-middle
Can read and alter the data

### What the adversary does (attack severity)
1. **Key recovery**

Severity: Critical

Attacker fully recovers the encryption key, giving them the ability to decrypt all messages encrypted with that key

2. **Full plaintext recovery**

Severity: High

Attacker recovers the complete plaintext of a specific encrypted message, compromising the message’s confidentiality

3. **Distinguishing attack**

Severity: Moderate

Attacker can identify patterns or tell if two ciphertexts correspond to the same or different plaintexts, revealing limited information about the data

### What the adversary knows
1. Ciphertext Only Attacks
    
    "the adversary gets to collect ciphertexts"

2. Known Plaintext Attacks
    
    "The adversary gets to know both the cipher texts and the plaintexts"

3. Chosen Plaintext Attacks
    
    "The adversary gets to choose plaintexts and get its respective ciphertext"
