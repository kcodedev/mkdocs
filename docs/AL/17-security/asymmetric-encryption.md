# Asymmetric Key Cryptography

![Asymmetric Encryption Diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f0/Asymmetric_encryption_scheme.png/960px-Asymmetric_encryption_scheme.png)

Asymmetric key cryptography, also known as public key cryptography, uses a pair of mathematically related keys: a public key for encryption and a private key for decryption.

## How Asymmetric Encryption Works
1. Each user generates a key pair (public key + private key)
2. Public keys are freely distributed
3. Private keys are kept secret
4. Anyone can encrypt data using someone's public key
5. Only the holder of the corresponding private key can decrypt the data

When sending a private message from the public to an individual or organization:

1. **Sender obtains recipient's public key** (published openly)
2. **Sender encrypts message** using the recipient's public key
3. **Encrypted message is sent** through any channel (email, post, etc.)
4. **Only the recipient** can decrypt using their private key

### Advantages
- No need for secure key exchange channels
- Enables secure communication between parties who have never met
- Supports digital signatures for authentication

### Disadvantages
- Slower than symmetric encryption
- Requires longer keys for equivalent security
- Higher computational requirements

## Hybrid Approach

Modern systems often combine both:

- Asymmetric keys encrypt the symmetric keys (secure key exchange)
- Symmetric keys encrypt the actual data (fast)
