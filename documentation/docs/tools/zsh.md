Oh My Zsh is an open source, community-driven framework for managing your zsh configuration.

```bash
sudo apt update
sudo apt install zsh
```

???+ example "Shell in Linux"

    Linux supports a variety of shells, each with its own features and use cases. Some of the most common shells include:

    1.  **Bash (Bourne Again Shell)**:
        -   Codename: `bash`
        -   Description: A widely used shell that is the default on many Linux distributions. It offers powerful scripting capabilities and is an enhanced version of the original Bourne Shell (`sh`).


    2.  **Zsh (Z Shell)**:
        -   Codename: `zsh`
        -   Description: An extended shell with advanced features like improved auto-completion, customizable prompts, and plugin support.


    3.  **Dash (Debian Almquist Shell)**:
        -   Codename: `dash`
        -   Description: A lightweight shell known for its speed and POSIX compliance. It is often used for script execution in Debian-based systems.


    4.  **Ksh (Korn Shell)**:
        -   Codename: `ksh`
        -   Description: A shell with features that combine aspects of the Bourne Shell (`sh`) and C Shell (`csh`). Known for its programming capabilities.


    5.  **Tcsh (TENEX C Shell)**:
        -   Codename: `tcsh`
        -   Description: An enhanced version of the C Shell (`csh`) with additional features like command-line editing and history.


    6.  **Fish (Friendly Interactive Shell)**:
        -   Codename: `fish`
        -   Description: Designed to be user-friendly and interactive, featuring syntax highlighting, autosuggestions, and a more intuitive command-line interface.


    7.  **Sh (Bourne Shell)**:
        -   Codename: `sh`
        -   Description: The ==original Unix shell==, which provides basic scripting capabilities. It is often used for simple scripts and is the basis for many other shells.




???+ success "Why Use zsh?"


    Here are some reasons why users might prefer zsh over other shells:

    1.  **Advanced Auto-Completion**: `zsh` offers more robust and customizable auto-completion than many other shells, making it easier to complete commands and file names.

    2.  **Customization**: `zsh` allows extensive customization of the command prompt and behavior, with support for various themes and plugins.

    3.  **Improved History Management**: Features like shared history across sessions and better history search make it easier to manage and reuse previous commands.

    4.  **Plugin Support**: With frameworks like `Oh My Zsh`, users can easily extend `zsh` with plugins for productivity, version control, and more.

    5.  **Powerful Scripting**: `zsh` includes advanced scripting capabilities that go beyond those found in bash, making it suitable for complex tasks.

    6.  **User-Friendly Features**: `zsh` has built-in features like spell correction, improved globbing (wildcard matching), and more, which can enhance the user experience.

    Overall, the choice of shell often comes down to personal preference and the specific features that a user finds most useful for their workflow.




???+ question "which shells are installed on your Linux"

    To determine which shells are installed on your Linux system, you can use the following methods:



    1.  **Check Installed Shells from `/etc/shells`**:

        The file `/etc/shells` lists all the shells that are available on the system. You can view its contents with:

        ```bash
        cat /etc/shells
        ```

        This file typically includes paths to various shells, such as `/bin/bash`, `/bin/zsh`, and `/bin/dash`.



    2.  **Check Available Shells Using `which` Command**:

        You can use the which command to see if a specific shell is installed. For example:

        ```bash
        which bash
        which zsh
        which fish
        ```

        If the command returns a path, the shell is installed. If it returns nothing, the shell is not installed.


    3.  **List All Installed Shells**:

        You can also search for all installed shells by listing the available executables in common shell directories:

        ```bash
        ls /bin /usr/bin | grep -E 'bash|zsh|sh|ksh|tcsh|fish'
        ```

        This will list the installed shells if they are located in `/bin` or `/usr/bin`.
    

    4.  **Check the Default Shell for Your User**:

        To see which shell your user is currently using as the default, you can use:

        ```bash
        echo $SHELL
        ```

        This will output the path to your current default shell.
    
    ---

    This will output the path to your current default shell.

---


## Reference

- [ohmyzsh: github](https://github.com/ohmyzsh/ohmyzsh/wiki)