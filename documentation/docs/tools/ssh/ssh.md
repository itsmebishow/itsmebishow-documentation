# SSH

!!! success

    GitHub typically uses the username **git** for SSH connections, regardless of your GitHub account username. This is because GitHub's SSH server ==recognizes you based on your SSH key==, not your GitHub username.

### How is SSH implemented in Windows?

There are two separate components of OpenSSH in Windows.

- an SSH client &
- an SSH server.

Microsoft implemented both in Windows using `OpenSSH Client` and `OpenSSH Server` respectively. And there are also two main methods to install and uninstall these components in Windows.
**The OpenSSH Client feature is installed by default in higher-end versions of Windows.** The Client is like the functionality of Putty. It allows you to make ‘client’ connections to other servers and devices using various secure protocols.

You can confirm if you have the client installed by opening a command prompt or PowerShell prompt and typing ‘ssh’ and hitting Enter.

![ssh-diagram](https://petri-media.s3.amazonaws.com/2021/11/Screenshot-2021-11-08-134530.png)

[for more information about ssh & OpenSSH using PowerShell...](https://petri.com/the-ultimate-guide-to-installing-openssh-on-windows/)

If you dont find the optional feature, then go to

```
1. Setting
2. App
3. App & Feature
3. search for optional feature
```

---

## Login remote with SSH key-based authentication

To log in to an SSH remote server without entering a password, you can set up SSH key-based authentication. Here's a step-by-step guide to do that:

!!! tip "1. Generate SSH Key Pair: (if you don't have one already)"

    ```sh title="bash"
    ssh-keygen -t rsa
    ```

    This command will generate a new SSH key pair (`public` and `private`)

!!! tip "2. Copy the Public Key to the Remote Server:"

    Use the ==ssh-copy-id== command to copy your public key to the remote server. Replace `username` and `remote_host` with your username and the hostname or IP address of the remote server.

    ```sh title="bash"
    ssh-copy-id username@remote_host
    ```

    You'll be prompted to enter your password for the remote server. After that, your public key will be added to the `~/.ssh/authorized_keys` file on the remote server.

!!! tip "3. Test SSH Connection:"

    Try to SSH into the remote server again. You should be able to log in without being prompted for a password:

    ```sh title="bash"
    ssh username@remote_host
    ```

With **SSH key-based authentication** set up, you can now log in to your remote server `without entering a password`, provided you have the corresponding private key stored on your local machine.


---

![SSH commands](../assets/video/GPygmfeXkAABEOX.jpeg)

---

## Reference

- [What is a Git SSH Key? ](https://www.atlassian.com/git/tutorials/git-ssh)
- [SSH Essentials: Working with SSH Servers, Clients, and Keys](https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys)
- [Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- [The Ultimate Guide to Installing OpenSSH on Windows](https://petri.com/the-ultimate-guide-to-installing-openssh-on-windows/)
- [jenkins guide](https://phoenixnap.com/kb/how-to-configure-docker-in-jenkins)

- [19 Common SSH Commands in Linux With Examples](https://phoenixnap.com/kb/linux-ssh-commands)
- [SSH Commands Cheat Sheet](https://stationx.net/ssh-commands-cheat-sheet/)
- [13 must-know SSH Commands](https://www.marcobehler.com/guides/ssh-commands#_scp)
