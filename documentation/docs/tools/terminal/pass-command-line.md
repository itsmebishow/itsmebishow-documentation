
![command line password manager](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj242XMHsgWX3dj0bXvl6x-SK53Qd5FCfNhfQ1v1qybT7vkPxgpfWQvlbLg_x5CxosyAA-bJU1q4EH5fhAIs_HUcTXTcELVaf0StDHo9eOyfkTi3SlwhMasVejsLymRe7zRZGSsHykgZDge/s1600/pass-command-line-password-manager.png)



## Using `pass` (Password Store)


The `pass` ==utility== is a password manager for Unix systems. It uses GPG for encryption.

### Installation

-   Install `pass`:

    ```bash
    $ sudo apt install pass
    ```

### Setup

???+ tips

    -   Initialize the password store:

        You need to initialize `pass` with a GPG key. If you don't have a GPG key, you can generate one:

        ```sh
        gpg --full-generate-key
        ```

        Follow the prompts to generate your key. Once you have a GPG key, initialize the password store with the key ID (replace `GPG_ID` with your actual key ID, which you can find using `gpg --list-keys`):

        ```sh
        pass init "GPG_ID"
        ```


### Storing a Password

???+ example

    -   Store a password:

        ```sh
        pass insert path/to/your/password
        ```

        For example:

        ```sh
        pass insert email/github
        ```

        You will be prompted to enter and confirm the password.



### Retrieving a Password

???+ abstract

    -   Retrieve a password:

        ```sh
        pass path/to/your/password
        ```

        For example:

        ```sh
        pass email/github
        ```

        This command will display the stored password.


### Managing Passwords

???+ tip

    -   List all stored passwords:

        ```sh
        pass
        ```

    -   Edit an existing password::

        ```sh
        pass edit path/to/your/password
        ```

        For example:

        ```sh
        pass edit email/github
        ```

    -   Remove a stored password::

        ```sh
        pass rm path/to/your/password
        ```

        For example:

        ```sh
        pass rm email/github
        ```




---


## Reference

- [manage-passwords-from-command-line](http://www.webupd8.org/2016/03/manage-passwords-from-command-line-with.html)
- [Manage your passwords in the Linux terminal](https://opensource.com/article/22/1/manage-passwords-linux-terminal)
- [Terminal Based Password Manager](https://medium.com/@johnnymatthews/terminal-based-password-manager-ab82fd8f856a)

