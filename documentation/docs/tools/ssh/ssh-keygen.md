# SSH Keygen

<!-- ## ssh-keygen -->

Let's break down the `ssh-keygen` command and explain each part:

```bash title="bash"
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

??? tip "Breakdown of the Command"

    1.  `ssh-keygen`:

        -   This is the command-line tool used to generate and manage SSH key pairs. It's part of the OpenSSH suite and is available on Linux, macOS, and Windows.


    2.  `-t rsa`:

        -   **Option**: `-t`

        -   **Purpose**: Specifies the ==type of key== to generate. In this case, it's set to `rsa`, which stands for Rivest-Shamir-Adleman. RSA is a widely used encryption algorithm for secure data transmission.

        -   **Alternative Types**: Other types include `dsa`, `ecdsa`, and `ed25519`. The choice depends on your security needs and compatibility requirements.


    3.  `-b 4096`:

        -   **Option**: `-b`

        -   **Purpose**: Specifies the number of bits in the key to create. In this case, it's set to `4096`, which is considered secure for RSA keys. A larger key size provides stronger encryption but may be slower to generate and use.

        -   **Default**: The default key size for RSA keys is typically `3072` bits.


    4.  `-C "your_email@example.com"`:

        -   **Option**: `-C`

        -   **Purpose**: Provides a comment for the key. This comment is appended to the public key and can help identify the key's purpose or owner. In this case, it's set to `"your_email@example.com"`, which is a common practice to associate the key with your email address.

**What the Command Does**

When you run this command, it generates a new RSA SSH key pair with the following characteristics:

- **Key Type**: RSA
- **Key Size**: 4096 bits
- **Comment**: Your email address

The command creates two files in the `.ssh` directory:

- **Private Key**: `id_rsa` (or a custom name if specified with `-f`)
- **Public Key**: `id_rsa.pub` (or a custom name with `.pub` extension if specified with `-f`)

You will be prompted to enter a passphrase to secure the private key. This is optional but recommended for added security. After generating the key pair, you can use the public key to authenticate with servers or services like GitHub.

---
