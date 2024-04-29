What is a daemon?

A daemon (pronounced `DAY-MAN`, `DAY-MON` or sometimes `DEE-MON`) is a background process that runs on the Linux OS continuously. When we say background, we mean that the program runs without any user interaction. It runs “behind the scenes“ so to speak.

## Basic

-   To see which `kernel version` is running on your system:

    ==The command “`uname`” stands for “Unix name” and tells you about the operating system kernel that’s running.==

    ```bash
    # display the operating system kernel that’s running:
    $ uname

    # display the kernel version number (the “release”):
    $ uname -r

    # display the machine hardware name:
    $ uname -m

    # display all available information:
    $ uname -a
    ```

-   To Open New Terminal in Ubuntu:

    ++ctrl+alt+t++

## White belt

-   To see the hostname:

    ```bash
    $ hostname

    # pwd or Print Working Directory
    $ pwd
    ```

-   To see your assigned `user id` and `group id`, simply issue the `id` command:

    ```bash
    $ id
    ```

## Black Belt

-   `Tmux`: Secret Background Windows

    `tmux` or `Terminal Multiplexer` is a piece of software used to manage terminal sessions. In addition, it can spin up long-standing terminals in the background of the Linux operating system that can be saved and recalled later.
    
    Tmux cancaome in handy for when you are doing work on a Linux system remotely via ==SSH== and need to keep a session open and to come back to later.

    ```bash title="bash"
    # install
    $ apt-get install tmux
    ```

---

## Cat Commands

Cat means `concatenate` frequently used command in Linux. It can read data from the file and gives the content as output. It can help us to `create`, `view` and `concatenate` files. 

So let us see frequently used `cat` commands.

```bash
# TO VIEW A SINGLE FILE:
$ cat filename

# TO VIEW MULTIPLE FILES
$ cat filename1 filename2

# TO VIEW THE CONTENTS OF A FILE PRECEDING WITH LINE NUMBERS:
$ cat -n filename

# TO CREATE A FILE
$ cat > new_file
```


Ubuntu Important Commands

```bash
# It gives information about how long the system has been running in one line.
$ uptime

# It displays detailed information about the users who are logged in the system currently.
$ w

# Using DNS Tools
# 1. It display information about the domain name, IP address & DNS server
$ nslookup www.google.com

# 2. It display information about the domain name & IP Addresss
$ host www.google.com

# 3. dig is a more advanced DNS tool
$ dig www.google.com
```

---

## Types of Packages

The two most popular packages

1.  Debian (`.deb`) packages:

    Debian packages are used for distributions like Debian, Ubuntu, and Linux Mint. 

2.  Red Hat (`.rpm`):
    
    Red Hat packages are used in Fedora, CentOS, RHEL, Suse, and others.

---

## Package Manager

1.  Debian package tool (**dpkg**): DPKG - The True Hero

    `Dpkg` is a tool that APT is using behind the scenes to install packages. `Dpkg` ==doesn’t install dependencies==. If we have a `.deb` package on our system, we can install it easily with dpkg:

    ```bash
    # install
    $ dpkg -i my_package_to_be_installed.deb

    # remove
    $ dpkg -r my_package_to_be_removed.deb

    # list
    $ dpkg -l
    ```

2.  **apt-get**

    ```bash
    # syntax
    $ apt-get install <package-name>

    $ apt-get install nmap
    ```


3.  Advanced Package Tool (**apt**)

    `apt` was introduced to be a bit more user-friendly than `apt-get`.
    APT builds on dpkg and adds some special features like managing dependencies, upgrades and searching for package

    ```bash
    # Keeping Software Up to Date
    $ sudo apt update
    ```

4.  Snap (**.snap**)

    Snap, a `package management system` developed by ==Canonical, Ltd==. Unlike `apt`
    packages, `snap` bundles all of the dependencies for a package into a single `.snap` file.  

    This ensures that the software package is self-contained with its own copy of all of the libraries and assets needed to run. This avoids the potential conflicts of packages relying on different versions of the same shared assets and libraries. The Snap system also allows different versions of the same packages to be installed in parallel.

    ```bash
    # Basic Snap Commands

    $ snap list
    $ snap install remmina
    $ snap remove remmina
    $ snap find vlc
    $ snap info remmina
    ```

---

## Tar (==Tape Archive==)

Tar is a powerful archiving utility used to compress and backup files in the Linux operating system. It is popular tool for creating `archives` of files and directories.

```bash
# To create a tar archive
$ tar -cvf archive.tar directory/

# To view the contents of a tar archive
$ tar -tvf archive.tar

# To extract the contents of a tar archive
$ tar -xvf archive.tar
```

- ‘`c`’ flag stands for `create`
- ‘`x`’ flag stands for `extract`
- ‘`t`’ flag stands for `list`
- ‘`v`’ stands for `verbose`
- ‘`f`’ stands for `file`

---

## File Permissions and Ownership

In Linux, every file and directory has an owner and a set of permissions that determine who can access and modify the file.

**File Permissions**

Each file on a Linux system has `three` types of permissions:

- read `r`, 
- write `w`, 
- execute `x`

```bash title="bash"
$ ls -l <file-or-folder>
```

**Changing File Permissions**

The `chmod` command is used to change the permissions for a file. 

```bash title="bash"
$ chmod mode <file-or-folder>
```

There are two ways to specify the mode: 

- using a `numeric value`, or 
- using `symbolic values`.

---

## Groups and id

1.  Creating a Group:

    To create a group, you can use the `groupadd` command followed by the name of the group you want to create. For example:

    ```bash title="bash"
    $ sudo groupadd developers
    ```

    This creates a new group called `developers`.

2.  Adding `Users` to a `Group`:

    To add users to a group, you can use the `usermod` command with the `-aG` option followed by the group name and username. For example:

    -   `-a`, `--append`: 

        This option tells `usermod` to append the user to the supplementary group(s). In other words, it adds the user to the specified group(s) without removing the user from any other groups.

    -   `-G`, `--groups`:
    
        This option specifies a list of supplementary groups which the user should become a member of. This option sets the list of supplementary groups directly, without appending to the current list of supplementary groups.

    So, when you use `-aG` together with usermod, it means you are appending the user to the specified group(s) without removing the user from any other groups, and you're specifying a list of supplementary groups which the user should become a member of.

    ```bash title="bash"
    $ sudo usermod -aG developers alice
    ```

    This adds the **user** `alice` to the `developers` **group**.

3.  Checking Group Membership:

    To see which `groups` a `user` belongs to, you can use the `id` command followed by the username. For example:

    ```bash title="bash"
    $ id alice
    ```

### To List all groups

To list all the groups in Linux, you can use the `getent` command followed by the `group` argument:

```bash title="bash"
$ getent group

# To check if the "docker" group already exists on your system,
# If the group doesn't exist, this command will not produce any output.
$ getent group docker

# This command will display all the groups that the user "bishow" is a member of.
$ groups bishow
```

Alternatively, you can also view the contents of the `/etc/group` file, which stores group information. You can use any text editor or commands like `cat` or `less` to view its contents:

```bash title="bash"
$ cat /etc/group

#
$ grep docker /etc/group
```

> Notes:

Choose whichever method is more convenient for you.


> Issue Solved:

==permission denied while trying to connect to the Docker daemon socket at `unix:///var/run/docker.sock`==

1.  Check Docker Socket Permissions:

    Ensure that the Docker socket file (`/var/run/docker.sock`) has appropriate permissions for the "docker" group to read and write to it. You can check and adjust the permissions using the following commands:

    ```bash title="bash"
    ls -l /var/run/docker.sock
    sudo chmod 666 /var/run/docker.sock
    ```

    The **first command** (`ls -l /var/run/docker.sock`) shows the current permissions, and the **second command** (`sudo chmod 666 /var/run/docker.sock`) grants read and write permissions to all users and groups.

2.  Restart Docker Service:

    Restart the Docker service to apply any changes to group memberships or permissions:

    ```bash title="bash"
    sudo systemctl restart docker
    ```

3.  Logout and Log Back In:

    If the above steps don't resolve the issue, try logging out and logging back in to refresh your session and apply any group membership changes:

    ```bash title="bash"
    logout
    ```

    Then log back in and try running `docker ps` again.

After performing these steps, try running `docker ps` again without sudo to check if the permission issue has been resolved. If you continue to encounter permission denied errors, further troubleshooting may be needed.

---


## Symlink `Linux`

A symlink (also called a `symbolic link`) is a type of file in Linux that points to another file or a folder on your computer. Symlinks are similar to shortcuts in Windows.

```bash
# Create a symlink to Director/Folder
$ ln -s /home/user/Folder <symlink-dir>

# Unlink or Remove a symlink
$ unlink <path-to-symlink>
$ rm <path-to-symlink>

# Find and Delete Broken Links
$ find /home/james -xtype l
$ find /home/james -xtype l -delete

# Check file/folder is symlink
$ ls -l <path-to-assumed-symlink>

# SOLVED: sysmlink error
# 1. Check the File/Folder is sysmlink corrupt or not
# $ ls -l <file/folder>
#
# 2. Unlink the Filer/Folder
# $ unlink <file/folder>
#
# 3. Create a File/Folder
# $ mkdir Documents
```

Reference

- [How to Create Linux Symlinks](https://www.linode.com/docs/guides/linux-symlinks/)
- [Symlink Tutorial in Linux](https://www.freecodecamp.org/news/symlink-tutorial-in-linux-how-to-create-and-remove-a-symbolic-link/)

---

![Iceberg Theory](https://www.mypspa.org/public/images/article/real/thumbs/alertpic_678345.jpeg)


---

!!! question "Linux"

!!! example "Pass (`ubuntu`)"

    pass is a very simple password store that keeps passwords inside `gpg`. It stores, retrieves, generates, and synchronizes passwords securely.

    ```bash title="bash"
    $ sudo apt update
    $ sudo apt install pass
    ```

??? example "`service` vs `systemctl`" 

    The commands sudo `service` and `systemctl` are both used for managing system services in Unix-like operating systems, but they have different purposes and usage patterns.

    1. **sudo service**:

          `sudo service` is a command-line tool used for managing services on Unix-like systems, ==particularly those using **SysVinit** as the init     system==. It provides a simple and consistent interface for starting, stopping, restarting, and querying the status of services.

          Usage:

          ```bash title="bash"
          # syntax
          $ sudo service <service_name> <action>

          #example
          $ sudo systemctl restart apache2
          ```

          The service command is often used in older Linux distributions that still use SysVinit as the init system.

    2. **systemctl**:

          `systemctl` is a command-line tool used for controlling the systemd system and service manager. ==`Systemd` is a modern init system== used by many     Linux distributions. systemctl allows you to manage services, units, targets, sockets, and more.

          Usage:

          ```bash title="bash"
          $ sudo systemctl <action> <service_name>
          $ sudo systemctl restart apache2
          ```

          `systemctl` provides more features and capabilities compared to `service`, and it's the preferred method for managing services on systems that use     systemd.

    In summary, if your system is using SysVinit as the init system, you would typically use `sudo service` to manage services. If your system is using systemd, `systemctl` is the preferred tool for service management. However, some distributions may provide compatibility layers or aliases to ensure compatibility between the two commands.


??? example "Creating a `User` ==without password=="

    Yes, you can add the `jenkins` user without setting a password. This is often done for system users that don't require interactive login, such as the     `jenkins` user used for automation tasks.

    To add the `jenkins` user without setting a password, you can use the useradd command with the `-r` (or `--system`) option, which creates a system user     without a password or home directory. Here's the command:

    ```sh title="bash"
    sudo useradd -r jenkins
    ```

    This command creates the `jenkins` user as a system user. ==System users are typically used for services and daemons and do not have passwords or home     directories by default==.

    After adding the user, you can proceed to grant the necessary permissions to the `jenkins` user, such as adding it to the 'docker' group if needed, to allow it to perform specific tasks without requiring a password.



??? example "groups & id in unix"

    To see the permissions of a user on a Unix-like system, you can use the `groups` command or `id` command.
    
    ```bash title="bash"
    # Syntax
    $ groups <username>
    $ id <username>
    
    # Example: ($USER refer to the currently logged-in user.)
    $ groups $USER
    ```


??? example "[Installing Xampp](https://phoenixnap.com/kb/how-to-install-xampp-on-ubuntu) in Linux"

      ```sh
      # To Launch XAMPP
      sudo /opt/lampp/./manager-linux-x64.run

      # To Unistall
      sudo /opt/lampp/./uninstall


      # After uninstall, remove the directory
      sudo rm -r /opt/lamp
      ```

      `sudo visudo` is a command used in Linux to edit the sudoers file, which determines who has administrative privileges on the system and what commands they can run with elevated permissions using the `sudo` command. The ==sudoers== file is crucial for system security, as it controls access to sensitive operations.

      Here's what each part of the command does:

      - `sudo`:

            This is a command used in Unix-like operating systems to allow users to run programs with the security privileges of another user (usually the `superuser`, or "`root`"). It stands for "superuser do."

      - `visudo`:

            This is a command-line utility specifically designed for editing the ==sudoers file==. It opens the sudoers file in a text editor, but it performs some syntax checking before saving changes to ensure that the file remains in a valid state. This helps prevent accidental misconfigurations that could lock users out of administrative access or potentially compromise system security.

      In summary, `sudo visudo` is used to safely edit the sudoers file, which is critical for managing user privileges and access control on a Linux system.

      - [How to Install and Use XAMPP on Ubuntu](https://itsfoss.com/install-xampp-ubuntu/)




---

## Reference

- [Shell Samurai by Stetson Blake](https://leanpub.com/shellsamurai-master-the-linux-command-line)
- [Linux Mastery: 100+ Exercises for Building Your Skills by Frank Anemaet](https://www.amazon.com/Linux-Mastery-Exercises-Building-Skills-ebook/dp/B0BTXNW913)

Blog

- [Install Docker Engine on Ubuntu 22.04](https://docs.docker.com/engine/install/ubuntu/)

Icebere Model

- [a systems thinking model: the iceberg](https://ecochallenge.org/iceberg-model/)
- [Iceberg Model](https://untools.co/iceberg-model/)