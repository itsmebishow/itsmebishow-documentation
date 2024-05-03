---
drafts: false
comments: true
date: 2024-01-25
tags: [Programming]
authors:
  - bishow
---

# A Guide to Secure Your Commits with GPG Keys

In the fast-paced world of software development, maintaining the integrity of your code is paramount. One powerful tool that helps ensure the authenticity of your commits is the GNU Privacy Guard (GPG). In this guide, we'll walk through the process of generating and using GPG keys to sign your commits, providing an extra layer of security for your projects.

<!-- more -->

## What is GPG?

GPG, or GNU Privacy Guard, is a free and open-source software that implements the OpenPGP standard for encrypting and signing data. In the context of version control systems like Git, GPG keys are used to sign commits, verifying that the person making the commit is who they claim to be.

## Step 1: Generating a GPG Key

The first step is to generate your GPG key. Open a terminal on your local machine and use the following command:

```bash title="bash"
gpg --full-generate-key
```

Follow the prompts to set up your key, providing your name, email address, and a strong passphrase. This passphrase is crucial, as it adds an additional layer of protection to your private key.

## Step 2: Adding Your GPG Key to GitHub

Once your GPG key is generated, you need to associate it with your GitHub account. Follow these steps:

1.  Copy your GPG key ID using the command:

    ```bash title="bash"
    gpg --list-secret-keys --keyid-format LONG
    ```

    > Terminology

    ```
    $ gpg --list-keys

    sec (Secret Key):
    ssb (Secret Subkey):
    uid (User ID):
    ```

2.  To display the ASCII-armored version of your public key, use the following command:

    ```bash title="bash"
    gpg --armor --export <YourKeyID>
    ```

    Replace `<YourKeyID>` with your actual GPG key ID.

3.  Go to your GitHub account settings, navigate to "SSH and GPG keys," and click on "New GPG key."

4.  Paste your GPG key ID and save it.

## Step 3: Configuring Git

Configure Git to use your GPG key by running:

```bash title="bash"
git config --global user.signingkey <GPG_KEY_ID>
```

Replace `<GPG_KEY_ID>` with your actual GPG key ID. Additionally, set Git to sign all of your commits by default:

```bash title="bash"
git config --global commit.gpgSign true
```

## Step 4: Signing Commits

From now on, every commit you make will be signed with your GPG key. You can sign a commit explicitly using:

```bash title="bash"
git commit -S -m "Your commit message"

```

## Verification and Visual Confirmation

GitHub will display a "`Verified`" badge next to signed commits on the web interface, providing a visual confirmation of the commit's authenticity. You can also verify commits locally using:

```bash title="bash"
git verify-commit <commit-SHA>
```

Replace `<commit-SHA>` with the actual SHA hash of the commit you want to verify.

By following these steps, you've empowered your version control workflow with an added layer of security. GPG keys not only help in ensuring the trustworthiness of your commits but also contribute to a more secure and transparent collaboration environment in the world of software development.

---

> Notes

When you run the **`gpg --list-keys`** command, you'll typically see output that looks like this:

```css
pub   4096R/<YourKeyID>  YYYY-MM-DD [expires: YYYY-MM-DD]
uid                  Your Name <your.email@example.com>
sub   4096R/<SubKeyID>  YYYY-MM-DD [expires: YYYY-MM-DD]

```

- `pub`: Public key information.
- `uid`: User ID (your identity associated with the key).
- `sub`: Subkey information.

The "`R`" in "`4096R`" denotes the key's algorithm (RSA in this case), and the key IDs ("`<YourKeyID>`" and "`<SubKeyID>`") are unique identifiers for the keys.

When you export the public key, you are essentially exporting the public part of the key pair, which includes the user ID information and the associated public subkey(s). The public key is what you can share with others, allowing them to encrypt messages or verify your digital signatures.

---

## Reference

- [Verified Commits on GitHub from Windows PC ( GPG Keys ) : youtube](https://www.youtube.com/watch?v=xj9OiJL56pM&ab_channel=AshishSinghBaghel)
