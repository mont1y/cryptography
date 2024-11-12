
# MAC 
A **MAC** (Message Authentication Code) is a small piece of information that’s used to verify both the integrity and authenticity of a message. In other words, a MAC ensures that the message has not been tampered with and that it was indeed sent by the correct sender.

How MAC Works:
Generate MAC:

The sender creates a MAC by combining the message with a secret key using a MAC algorithm (e.g., HMAC).
This results in a short, fixed-length code (the MAC) that is sent along with the message.
Verify MAC:

When the receiver gets the message and the MAC, they use the same secret key to generate a MAC on their end.
If the MAC they generate matches the one received, it confirms that the message is authentic and hasn’t been altered.
Key Features of MAC:
Integrity: Any changes to the message would result in a different MAC, allowing the receiver to detect tampering.
Authentication: Only someone with the secret key can generate a valid MAC, confirming the sender’s identity.

# Definition of CMA Secure Message Auth Codes
Rough definition: A polynomial time adversary cannot forge a message of its
own choosing, even if the adversary has the power to choose messages and
see their tags.

Actual definition: Let n be the security parameter (usually the key
length) of the scheme

We say that the MAC scheme is secure if for every poly-time Adv, then
Pr[Adv outputs m*,t* such that Verk
(m*,t*) = 1 ] ~ 2-n