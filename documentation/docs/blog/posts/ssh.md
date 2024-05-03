---
draft: false
tags: [Programming]
comments: true
date: 2024-01-12
authors:
  - bishow
---

# How to Add SSH Keys to Your GitHub Account

SSH, which stands for Secure Shell, is a cryptographic network protocol used to securely access and manage network devices and servers over a potentially unsecured network. It provides a secure way to log into and communicate with a remote machine, allowing users to execute commands on the remote machine and transfer files between the local and remote machines.

<!-- more -->

Key-based Authentication:

Using SSH keys is a more secure and convenient way to authenticate without entering a password every time.

=== "Beginner"

    ## Step 1: Generate SSH Key

    1.  Open a terminal on your local machine.

    2.  Run the following command to generate a new SSH key. Replace "your_email@example.com" with your actual GitHub email address.

        ```bash title="bash"
        ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
        ```

        Press Enter to accept the default file location (`~/.ssh/id_rsa`) and optionally set a passphrase for additional security.

    ## Step 2: Add SSH Key to SSH Agent

    1.  Start the SSH agent:

        ```bash title="bash"
        eval $(ssh-agent -s)
        ```

    2.  Add your SSH private key to the SSH agent:

        ```bash title="bash"
        ssh-add ~/.ssh/id_rsa
        ```

    ## Step 3: Add SSH Key to GitHub

    1.  Display the contents of your public key:

        ```bash title="bash"
        cat ~/.ssh/id_rsa.pub
        ```

        Copy the entire key that is displayed in the terminal.

    2.  Open your GitHub account in a web browser.
    3.  Go to "Settings" > "SSH and GPG keys" > "New SSH key."
    4.  Paste your SSH key into the "Key" field, give it a title (for example, "My SSH Key"), and click "Add SSH Key."

    ## Step 4: Test SSH Connection

    To verify that everything is set up correctly, you can test the SSH connection to GitHub:

    ```bash title="bash"
    ssh -T git@github.com
    ```

    If successful, you will see a message indicating that you've successfully authenticated.

=== "Multiple Accounts (Advanced)"

    **Generating SSH Keys**

    1.  Generate SSH Keys for Each GitHub Account:

        - Open a Git Bash terminal on your Windows machine.
        - Generate a new SSH key for each GitHub account:

        ```bash title="bash"
        ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
        ```

        Provide a unique name for each key pair, for example, `id_rsa_personal` and `id_rsa_work`.

    2.  Add SSH Keys to the SSH Agent:

        - Start the SSH agent:

        ```bash title="bash"
        eval $(ssh-agent -s)
        ```

        - Add your private keys to the SSH agent:

        ```bash title="bash"
        ssh-add ~/.ssh/id_rsa_personal
        ssh-add ~/.ssh/id_rsa_work
        ```

    3.  Configure SSH Config File:

        - Create or edit the ~/.ssh/config file using a text editor:

        ```bash title="bash"
        nano ~/.ssh/config
        ```

        - Add the following configuration to associate each SSH key with the respective GitHub account:

        ```text title="plaintext"
        # Personal GitHub account
        Host github.com
            HostName github.com
            User git
            IdentityFile ~/.ssh/id_rsa_personal

        # Work GitHub account
        Host github-work
            HostName github.com
            User git
            IdentityFile ~/.ssh/id_rsa_work
        ```

        Make sure to replace `id_rsa_personal` and `id_rsa_work` with your actual key filenames.

    4.  Update Git Config:

        - Configure your global Git settings to use the specified hosts:

        ```bash title="bash"
        git config --global user.name "Your Personal Name"
        git config --global user.email "your_email@example.com"
        ```

        Repeat the above command with the appropriate values for your work account.

    5.  Test SSH Connection:

        Test the SSH connection to GitHub:

        ```bash title="bash"
        ssh -T git@github.com
        ```

    **Adding SSH in Github**

    1.  Copy the SSH Public Key:

        Copy the contents of your SSH public key for each account. You can use the following command to print the public key to the terminal:

        ```bash title="bash"
        cat ~/.ssh/id_rsa_personal.pub
        ```

        ```bash title="bash"
        cat ~/.ssh/id_rsa_work.pub
        ```

    2.  Add SSH Key to GitHub:

        - Log in to your GitHub account.
        - Navigate to "Settings" > "SSH and GPG keys."
        - Click on "New SSH key" or "Add SSH key."
        - Provide a title (e.g., "Personal SSH Key" or "Work SSH Key").
        - Paste the copied public key into the "Key" field.
        - Click "Add SSH Key" or "Save SSH Key."
        - Repeat the process for both your personal and work GitHub accounts.

    Now, when you interact with GitHub using Git commands over SSH, GitHub will recognize your SSH keys and authenticate your access.

    **Git Config**

    1.  Set Up Global Git Config:

        ```bash title="bash"
        git config --global user.name "Your Personal Name"
        git config --global user.email "personal@gmail.com"
        ```

    2.  Set Up Local Git Config for Work Repositories:

        ```bash title="bash"
        cd /path/to/work/repo
        git config user.name "Your Work Name"
        git config user.email "work@gmail.com"
        ```

---

> Notes

```bash title="bash"
git config --global --get user.name
git config --global --get user.email
```

---
