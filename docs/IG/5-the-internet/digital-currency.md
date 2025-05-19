# Digital Currency and Blockchain 💸🔗

---

## 💰 What is Digital Currency?

A **digital currency** is a form of money that exists only in electronic form — there are no physical coins or banknotes. Examples include:

- 💳 Online payment systems (e.g. PayPal, eWallets)
- 🪙 Cryptocurrencies (e.g. Bitcoin, Ethereum)

Digital currencies can be used to:

- Buy goods and services online 🛒
- Send money across borders 💸
- Store value in digital wallets 📲

---

## What is Blockchain? 📚⛓️

Blockchain is like a **digital ledger** (a special record book) that keeps track of all digital currency transactions. It’s a list of records called **blocks** that are linked together in a chain.

### How Does It Work?

- Each **block** contains a list of recent transactions.
- Each block has a **unique code** called a **hash** — like a digital fingerprint. 🕵️‍♂️✨
- Every new block includes the hash of the previous block, which links them together securely.  
- This makes it **almost impossible to change** any transaction once it’s added because changing one block would break the chain. 🛡️🔒

---

## What is Hashing? 🔢🔐

Hashing is like turning information into a special number — a **hash value** — using a mathematical formula. This number is used to uniquely represent the original information.

Here's a **toy example** of how hashing might work:

Let’s say our hash function is:

-> HASH(x) = (sum of character codes of x) mod 100


🧪 Try hashing the word `"cat"`:

- `c` = 99  
- `a` = 97  
- `t` = 116  
- Sum = 99 + 97 + 116 = 312  
- Hash = 312 mod 100 = **12**

Now hash `"bat"`:

- `b` = 98  
- `a` = 97  
- `t` = 116  
- Sum = 98 + 97 + 116 = 311  
- Hash = 311 mod 100 = **11**

See how just changing one letter completely changes the hash value? Even though `"cat"` and `"bat"` are very similar, their hashes are different.

---

### Why is Hashing Useful? 🔐

- It creates a unique "digital fingerprint" of the data.
- Even the tiniest change results in a completely different hash.
- This helps detect tampering or errors in data.

In real blockchains, hash functions are **much more complex** and secure, producing very long hash values (often 64 characters in hexadecimal format).


---

## Why is Blockchain Secure? 🔐

Because each block links to the previous block's hash, trying to tamper with one block would require changing **every** following block. This requires huge amounts of computing power, so it’s very secure!

---

## Fun Fact! 🎉

Blockchain isn’t just for digital currencies — it’s also used in supply chains, voting systems, and even to prove the authenticity of art! 🖼️✅

## ⛓️ Summary

- Digital currencies are electronic-only money 💸
- Blockchain is a tamper-proof ledger that secures cryptocurrencies 🔒
- Hashing turns information into unique fingerprints and protects data integrity 🧬

