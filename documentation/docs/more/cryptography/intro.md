



```
Cryptography
│
├── Symmetric Key Cryptography
│   ├── AES
│   ├── DES
│   └── 3DES
│
├── Asymmetric Key Cryptography
│   ├── RSA
│   ├── ECC
│   └── ElGamal
│
├── Hash Functions
│   ├── SHA-256
│   ├── MD5
│   └── SHA-3
│
├── Digital Signatures
│   ├── RSA Digital Signatures
│   └── ECDSA
│
├── Cryptographic Protocols
│   ├── TLS/SSL
│   └── IPsec
│
└── Public Key Infrastructure (PKI)
    ├── Certificate Authorities (CAs)
    ├── Registration Authorities (RAs)
    └── X.509 Certificates
```



---


???+ tip "Explain to 5 year old, what is Symmetric and Asymmetric Key Cryptography "

    Alright, let's imagine a simple way to understand symmetric and asymmetric key cryptography using a fun analogy:

    **Symmetric Key Cryptography: The Secret Code**

    Imagine you have a special box that can only be opened with a secret key.

    -   Symmetric Key: You and your friend both have the same secret key to open the box. This key is like a special code that only you two know.
    -   How it Works:
        -   Locking the Box: You put a toy inside the box and lock it with the key.
        -   Unlocking the Box: Your friend uses the same key to open the box and see the toy inside.

    So, both of you need the same key to lock and unlock the box. If someone else finds the box but doesn’t have the key, they can’t open it.


    **Asymmetric Key Cryptography: The Magic Lock**

    Now, imagine you have a magic lock with two keys – one to lock and another to unlock.

    -   Asymmetric Keys:
        -   Public Key: This key is like a special lock you can give to everyone. Anyone can use it to lock the box.
        -   Private Key: This is the special key you keep secret. Only you can use this key to unlock the box.

    -   How it Works:
        -   Locking the Box: Anyone who has the public key can lock the box, but they can’t open it.
        -   Unlocking the Box: Only you, with the private key, can unlock the box and see what’s inside.

    So, people can send you secret things by locking them with the public key, and only you can unlock them with your private key.


    ---


    **Summary**

    -   **Symmetric Key**: Same key for locking and unlocking (like a shared secret code).
    -   **Asymmetric Key**: Different keys for locking and unlocking (like a magic lock with one key that everyone can use to lock, and a special key that only you can use to unlock).
    
    This way, both types of keys help keep your secrets safe, but they work in different ways!






---


## Reference

- [Cryptography and its Types](https://www.geeksforgeeks.org/cryptography-and-its-types/)



