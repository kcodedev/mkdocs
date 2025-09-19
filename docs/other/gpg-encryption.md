# GPG: Keeping Your Messages and Files Safe

GPG (GNU Privacy Guard) is a tool that lets you **encrypt** (lock) and **decrypt** (unlock) files or messages so only the intended person can read them.

---

## What is GPG?

* It uses **encryption** to make your messages unreadable to anyone without the right key.
* There are **two main types of encryption**:


1. **Symmetric encryption** – same password to lock and unlock.
2. **Asymmetric encryption** – uses a **key pair**:

      * **Public key**: anyone can use it to encrypt messages to you.
      * **Private key**: only you can use it to decrypt messages.

---

## Symmetric Encryption

Encrypt a file or message using a password:

```bash
gpg -c secret.txt
```

* `-c` means **symmetric encryption** (password-based).
* GPG asks for a strong passphrase.
* Output: `secret.txt.gpg` (encrypted file).

Decrypt it:

```bash
gpg -d secret.txt.gpg > secret.txt
```

* Enter your password.
* Now the original file is readable again.

---

## Asymmetric Encryption

1. **Generate your key pair**:

```bash
gpg --full-generate-key
```

* Follow the prompts to create a **public key** and a **private key**.
* Keep your **private key** secret!

2. **Share your public key** with friends:

```bash
gpg --export -a YourName > mypublickey.asc
```

* Send `mypublickey.asc` to someone who wants to send you encrypted messages.

3. **Import someone else's public key**:

```bash
gpg --import friendspublickey.asc
```
* This adds their public key to your keyring so you can encrypt messages for them.

* List your keys to see what's available:

```bash
gpg --list-keys          # List all public keys
```

4. **Encrypt a message for someone else** using their public key:

```bash
gpg --encrypt --recipient FriendName message.txt
```

* Output: `message.txt.gpg` – only your friend can decrypt it.

5. **Decrypt a message sent to you** using your private key:

```bash
gpg --decrypt message.txt.gpg > message.txt
```

* Enter your private key passphrase if prompted.
* Now the message is readable.

---

## Why Asymmetric Encryption

* Anyone can send you a secure message using your public key.
* Only your private key can decrypt it.
* You never have to share your private key.
* Even if someone intercepts the message, they cannot read it.

---

## Tips for Safe Use

* **Keep your private key secret** – don’t email it or store it in public places.
* Use a **strong passphrase** for your private key.
* Backup your keys somewhere safe.
* Use GPG for personal messages, homework submissions, or sensitive files.

---

> **Fun fact:** Asymmetric encryption is the same type of encryption used in secure websites (HTTPS) and messaging apps like Signal.
