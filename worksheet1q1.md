# Cryptography Worksheet 1 CPA (Chosen Plaintext Attack) Question 1 Walkthrough

Consider an encryption scheme where the first bit of a message is equal to the last
bit of its ciphertext.
This encryption scheme is not perfectly secure - show an attack.

#### Semantic Security Game:

In cryptography, a semantic security game is an experiment involving a **challenger** and an **adversary**. The game determines the security of the encryption scheme.

#### Definition of CPA Secure Encryption:
A polynomial time adversary cannot perform a distinguishing attack even if he has the power to choose plaintexts and see their encryptions.

In other words, the challenger encrypts two different messages the adversary chooses, and the adversary should **not** be able to distinguish which ciphertext corresponds to which message. If the attacker is able to do so accurately, the encryption scheme is not perfectly secure.

## Solution

![graph shown in q1](q1graph.png "Question1SemanticGraph")

### Breakdown

---

### Challenger and Adversary:

The diagram is divided into two columns. The left column (Challenger) represents the encryption process, and the right (Adversary) represents the attacker.

The interaction between them shows a semantic security game, where they exchange messages to test the encryption scheme's security.

### 1. 𝑘 ←$ 𝐾

The Challenger selects a random secret key 𝑘 from the key space 𝐾 used to encryption later on. The symbol `←$` means "select at random from."

### 2. m $_{0}$ ← 0 || random bits

The adversary constructs a message (plaintext) m $_{0}$ that begins with a 0 bit followed by random bits.

Note: || represents concatenation, meaning the 0 or 1 is joined with a sequence of random bits to form the message

### 3. m $_{1}$ ← 1 || random bits

The adversary constructs another message m $_{1}$ that begins with a 1 bit followed by random bits.

### 4. Sending the plaintext
Adversary sends the message (plaintext) to the challenger

After constructing the messages m $_{0}$ and m $_{1}$, The adversary sends the message to the attacker.

### 5. c ← Enc(k,m $_{b}$)

The challenger chooses one of the messages the adversary sends randomly {0 or 1}, and encrypts the messages with the secret key 𝑘.

### 6. Sending the ciphertext
Challenger sends the encrypted message (ciphertext) to the adversary

### 7. $ \hat{b} \leftarrow $ 0 if c[-1] = 0 else 1

The adversary tries to guess which message the challenger encrypted.


$ \hat{b} $ represents the bit of the message that the challenger chose at random (i.e. which message the challenger encrypted {0 or 1}).

Since the encryption scheme states that the first bit of a message is equal to the last bit of its ciphertext, we can deduct that, if the last bit of the ciphertext c (denoted by c[-1]) == 0, the message encrypted was m $_{0}$.

Vice versa, if the last bit of the ciphertext c (denoted by c[-1]) == 1, the message encrypted was m $_{1}$.

Therefore,

**SSAdv(A, E) = |Pr[A outputs 1 in experiment 0] − Pr[A outputs 1 in experiment 1]| = |0 − 1| = 1**

Breakdown:

The semantic security advantage (**SSAdv**)

of an adversary A against an encryption scheme E (**SSAdv(A,E)**)

is equal to the absolute value of 

the probability of adversary A guesses that the message encrypted was m $_{1}$ when it's actually m $_{0}$ (which is zero, because the adversary can tell which message was encrypted very easily just by looking at the last bit)

minus

the probability of adversary A guesses that the message encrypted was m $_{1}$ when it is indeed m $_{1}$ (which is 100%, or 1)

Since the adversary can distinguish which message was encrypted accurately, we can conclude that the encryption scheme is **not** semantically secure.

