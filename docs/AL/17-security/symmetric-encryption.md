# Symmetric Encryption

![Symmetric Encryption Diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/8/80/Simple_symmetric_encryption-en.svg/640px-Simple_symmetric_encryption-en.svg.png)

## Introduction

Encryption is the process of converting readable data (plaintext) into an unreadable format (ciphertext) to protect sensitive information from unauthorized access. This fundamental security technique ensures that even if data is intercepted, it cannot be understood without the proper decryption key. Encryption plays a crucial role in modern digital communications, protecting everything from personal emails to financial transactions and government communications.

## Symmetric Key Cryptography

Symmetric key cryptography, also known as secret key cryptography, uses the same key for both encryption and decryption. This method is fast and efficient for encrypting large amounts of data.

### How Symmetric Encryption Works
1. Both sender and receiver share the same secret key
2. The sender encrypts the plain text using the shared key
3. The encrypted cipher text is transmitted
4. The receiver decrypts the cipher text using the same shared key

### Advantages of Symmetric Key Cryptography
- Very fast encryption/decryption speeds
- Efficient for large data volumes
- Lower computational requirements

### Disadvantages
- Key distribution problem: How to securely share the secret key?
- Each pair of users needs a unique key
- Not suitable for scenarios where public key exchange isn't feasible

## Symmetric Encryption/Decryption Processes
1. **Encryption**: Plain text + Secret Key → Cipher text
2. **Decryption**: Cipher text + Secret Key → Plain text
3. **Key requirement**: Same key used for both operations