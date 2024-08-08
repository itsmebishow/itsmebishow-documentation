
!!! success "Deployment"

    <!-- ## Deployment -->

    ```
    my-project/
        mkdocs.yml
        docs/
    orgname.github.io/

    $ cd ../orgname.github.io/
    $ mkdocs gh-deploy --config-file ../<project-name>/mkdocs.yml --remote-branch <branch-name>
    ```

!!! note

    To Preview ==markdown== in `vs code`

    ++ctrl+shift+v++

## **Python**

### shell

!!! example

    ```bash
    # ~=4.2 allows installing any version of Django that is in the 4.2 series, 
    # but it prevents installing versions from Django 4.3 or higher.
    $ pip install django~=4.2

    # Install djagno, drf, dotenv, mysqlclient at once
    $ pip install django djangorestframework python-dotenv mysqlclient

    # open python shell
    $ python manage.py shell

    # create the object using the model
    $ from geeks.models import GeeksModel
    $ GeeksModel.objects.create(title="title1",description="description1").save()
    $ GeeksModel.objects.create(title="title2",description="description2").save()
    ```

### venv

```sh
# On Linux
python3 -m venv venv && source venv/bin/activate

# On Windows
.\venv\Scripts\activate
```

## **git**

`Global Information Tracker`

### Basic

```bash
# used to make changes to the last commit
$ git commit --amend -m "Add"

# restore all files to the state of the last commit.
$ git restore *

# Managing remote repositories
$ git remote -v

# showing each commit as a single line
$ git log --oneline

# The primary difference is that --pretty=oneline explicitly specifies the format to be "oneline."
$ git log --pretty=oneline

# if you want to delete a remote branch named feature-branch, you would use:
$ git push origin --delete feature-branch
```

### configuration

```bash
# opens the global configuration file
git config --global --edit

# opens the repository-specific configuration file
git config --edit
```

### git branch

```bash
# displaying very-verbose information
$ git branch -vv

# used to list all branches in a Git repository, both local and remote branches.
$ git branch -a

# To see only remote branches
$ git branch -r

# To see only local branches
$ git branch
```

### git diff

```bash
# To see the changes made to a specific file in Git
git diff path/to/your/file

# To see the changes for a file that has already been staged (but not committed yet)
git diff --staged path/to/your/file

# If you want to display only the names of the files that have changed
git diff --name-only

# If you just want a summary of changes:
git diff --stat

```

### git stash

```bash
# Stashing is helpful when you want to save changes in your working directory without committing them
# This is useful when you need to switch branches or perform other operations without committing incomplete work.
$ git stash save "your message"

# Lists all stashes
$ git stash list

# Removes all stashes.
$ git stash clear

# Applies the changes from the most recent stash and removes it from the stash list.
$ git stash pop

# Applies the changes from the most recent stash to your working directory.
$ git stash apply

# Creates a new branch and applies the changes from the most recent stash to it.
$ git stash branch feature-branch

```

### git cherry-pick

```bash
# allows you to apply a specific commit from one branch onto another. 
# This is useful when you want to selectively bring changes from 
# one branch to another without merging the entire branch.

$ git cherry-pick <commit>
```


### git tag

??? example "git tags"

    To add a tag in Git, you have ==two main options==: **lightweight tags** and **annotated tags**.

    **1. Lightweight Tags:**

    Lightweight tags are simply pointers to a specific commit. They are created with the git tag command followed by the tag name. Here's how you can add a lightweight tag:

    ```bash
    git tag <tag_name>
    ```

    For example, if you want to tag the current commit with the tag "v1.0.0", you would run:

    ```bash
    git tag v1.0.0
    ```

    **2. Annotated Tags:**

    Annotated tags, on the other hand, are stored as full objects in the Git database. They include a tagger name, email, date, and a tagging message. You create an annotated tag using the -a option with the git tag command, like so:

    ```bash
    git tag -a <tag_name> -m "Tagging message"
    ```

    ```bash
    git tag -a v1.0.0 -m "Version 1.0.0 release"
    ```

    ---

    **Pushing Tags to Remote Repository:**

    After creating the tag locally, you might want to push it to a remote repository like GitHub. You can do this using the git push command with the --tags option to push all tags:

    ```bash
    git push origin --tags
    ```

    If you only want to push a specific tag, you can specify it like this:

    ```bash
    git push origin <tag_name>
    ```

    For example:

    ```bash
    git push origin v1.0.0
    ```

    ---

    ==Example Workflow:==

    Here's a complete example workflow to add a tag and push it to a remote repository:

    1. Create a lightweight tag:

    ```bash
    git tag v1.0.0
    ```

    2. Push the tag to the remote repository:

    ```bash
    git push origin v1.0.0
    ```

    **Alternatively, if you want to create an annotated tag:**

    1. Create an annotated tag with a message:

    ```bash
    git tag -a v1.0.0 -m "Version 1.0.0 release"
    ```

    2. Push the annotated tag to the remote repository:

    ```bash
    git push origin v1.0.0
    ```


    Remember to replace `<tag_name>` with the name of your tag and `<tagging_message>` with a descriptive message for annotated tags.

---

### git log

!!! note

    ```bash
    ## Oneline
    git log —oneline

    ## Decorating 
    git log --oneline --decorate

    ##  Filtering the commit history
    
    # 1. By date 
    git log --after="2020-15-05"
    git log --after="2020-15-05" --before="2020-25-05"
    git log --before="10 day ago"

    # 2. By author
    git log --author="Srebalaji"

    ## diff between branches
    git log master..develop
    ```

    ---

    > Reference

    - [Ten Useful Git Log Tricks ](https://hackernoon.com/ten-useful-git-log-tricks-7nt3yxy)
    - [5 Git Tricks Every Developer Should Know ](https://dev.to/shadid12/5-git-tricks-every-developer-should-know-1201)
    - [Advanced Git log ](https://www.atlassian.com/git/tutorials/git-log)
    - [Git Log Tricks You Might Not Know](https://blog.devgenius.io/git-log-tricks-you-might-not-know-4cf2b746d1b7)


!!! tip "shortcuts"

    ```bash
    git log --after="yesterday" --oneline
    ```


---

## Git Directives

In Git, "directives" typically refer to commands or instructions used to perform various operations within the version control system. Here are some common Git directives:

- **git init**: Initializes a new Git repository in the current directory or in a specified directory.

- **git clone**: Creates a local copy of a remote repository.

- **git add**: Adds changes in the working directory to the staging area.

- **git commit**: Records changes in the staging area to the repository.

- **git push**: Uploads local repository content to a remote repository.

- **git pull**: Fetches changes from a remote repository and merges them into the current branch.

- **git fetch**: Downloads objects and references from another repository.

- **git merge**: Combines multiple sequences of commits into one unified history.

- **git branch**: Lists, creates, or deletes branches.

- **git checkout**: Switches branches or restores working tree files.

- **git status**: Displays the state of the working directory and the staging area.

- **git log**: Shows the commit logs.

- **git remote**: Manages connections to remote repositories.

- **git reset**: Resets the current HEAD to the specified state.

- **git rebase**: Reapplies commits on top of another base tip.

- **git tag**: Creates, lists, deletes, or verifies a tag object signed with GPG.


## Git Categorywise

!!! tip "Initialization and Configuration"

    - git init: Initializes a new Git repository.
    - git config: Configures settings for Git, such as user name and email.

!!! tip "Managing Changes"

    === "Staging Changes"
    
        - git add: Adds changes from the working directory to the staging area.
        - git rm: Removes files from both the working directory and the index.
        - git mv: Moves or renames files, updating the index accordingly.

    === "Committing Changes"

        - git commit: Records changes from the staging area to the repository.
        - git commit --amend: Amends the last commit by adding changes or modifying the commit message.


!!! tip "Branching and Merging"

    === "Branching"

        - git branch: Lists, creates, renames, or deletes branches.
        - git checkout: Switches branches or restores working tree files.
        - git switch: Switches branches or restores working tree files (==Git 2.23+==).
        - git restore: Restores working tree files (==Git 2.23+==).

    === "Merging"
    
        - git merge: Combines changes from different branches into the current branch.
        - git rebase: Reapplies commits from one branch onto another, often used for cleaner history.

!!! tip "Remote Repository Interaction"

    === "Remote Repositories:"
    
        - git clone: Clones a repository into a new directory.
        - git remote: Manages connections to remote repositories.
        - git fetch: Downloads objects and references from another repository.
        - git pull: Fetches changes from a remote repository and merges them into the current branch.
        - git push: Uploads local repository content to a remote repository.

!!! tip "Inspection and Comparison"

    === "Viewing Changes"
    
        - git status: Shows the status of the working directory and the staging area.
        - git diff: Shows changes between commits, commit and working tree, etc.
        - git log: Displays commit history.
        - git show: Shows information about a specific commit.

    === "Tagging"
    
        - git tag: Creates, lists, deletes, or verifies tags in the repository.

!!! tip "Undoing Changes"

    === "Reverting Changes"

        - git reset: Resets the current HEAD to the specified state.
        - git revert: Creates a new commit that undoes changes made by a previous commit.

!!! tip "Collaboration"

    === "Submodules"

        - git submodule: Manages project submodules.

!!! tip "Miscellaneous"

    === "Utilities"

        - git clean: Removes untracked files from the working directory.
        - git stash: Temporarily shelves changes so you can work on something else.
        - git grep: Searches through the contents of files in your Git repository.
        - git bisect: Helps to find the commit that introduced a bug by binary search.

These categories cover the major functionalities of Git and provide a structured overview of its directives.



---

## SSH Directives

SSH (Secure Shell) directives, like Git directives, are commands or instructions used to perform various operations related to SSH connections and configuration. Here are some common SSH directives:

- **ssh**: The basic command to initiate an SSH connection to a remote server. For example, ssh username@hostname.

- **ssh-keygen**: Generates a new SSH key pair (public and private keys) for authentication.

- **ssh-copy-id**: Copies the public SSH key to a remote server's authorized_keys file, allowing passwordless SSH authentication.

- **ssh-add**: Adds private keys to the SSH authentication agent, enabling seamless authentication without entering passphrases repeatedly.

- **ssh-agent**: Starts the SSH authentication agent, which manages private keys used for authentication.

- **ssh-keyscan**: Gathers SSH server host keys and adds them to the local known_hosts file.

- **ssh-config**: Configures SSH client behavior, allowing customization of connection parameters and aliases for hosts.

- **scp**: Securely copies files between hosts over an SSH connection.

- **sftp**: Interactive file transfer over an SSH connection, providing a secure alternative to FTP.

- **sshfs**: Mounts a remote filesystem over SSH, allowing access to remote files as if they were local.

These directives are essential for managing SSH connections, keys, and configurations, ensuring secure and efficient communication between client and server systems.

---

## SSH Directives Categorywise

Certainly! SSH directives can be categorized based on their functions and the aspects of SSH configuration they control. Here's a categorization of SSH directives:


!!! tip "Connection Configuration"

    - Host: Specifies the host(s) to which the following directives apply.
    - HostName: Specifies the actual hostname or IP address of the remote server.
    - User: Specifies the username to use when connecting to the remote host.
    - Port: Specifies the port number to use for SSH connections.

!!! tip "Authentication and Authorization"

    - IdentityFile: Specifies the path to the private key file for authentication.
    - IdentityAgent: Specifies the path to the SSH authentication agent socket.
    - ForwardAgent: Enables SSH agent forwarding, allowing authentication credentials to be forwarded to remote hosts.
    - ProxyJump: Specifies one or more jump hosts to use as intermediaries for reaching the destination host.
    - ProxyCommand: Specifies the command to use for establishing a connection to the destination host through a proxy.


---


##  SSH configuration directives

The SSH configuration file, often located at `~/.ssh/config` or `/etc/ssh/ssh_config`, allows users to customize SSH client behavior by defining various directives. Here are some common directives found in the SSH configuration file:

1.  Host: Specifies the host(s) to which the following directives apply. This can be a hostname, IP address, or wildcard pattern.

    ```bash title="Example"
    Host example.com
    HostName 192.0.2.1
    User john
    ```

2.  HostName: Specifies the actual hostname or IP address of the remote server.

3.  User: Specifies the username to use when connecting to the remote host.

4.  Port: Specifies the port number to use for SSH connections.

5.  IdentityFile: Specifies the path to the private key file for authentication.

6.  IdentityAgent: Specifies the path to the SSH authentication agent socket.

7.  ProxyJump: Specifies one or more jump hosts to use as intermediaries for reaching the destination host.

8.  ProxyCommand: Specifies the command to use for establishing a connection to the destination host through a proxy.

9.  ForwardAgent: Enables SSH agent forwarding, allowing authentication credentials to be forwarded to remote hosts.

10. LogLevel: Specifies the verbosity level for logging SSH client activity.

11. Compression: Enables compression of SSH data to reduce bandwidth usage.

12. ServerAliveInterval / ServerAliveCountMax: Specifies the interval and maximum number of server-alive messages sent to prevent connection timeouts.

13. BatchMode: Disables password authentication and forces SSH to exit if public key authentication fails.

14. StrictHostKeyChecking: Controls how SSH handles unknown or changed host keys.

15. UserKnownHostsFile: Specifies the path to the file containing known host keys.

16. TCPKeepAlive: Enables TCP keep-alive messages to prevent connections from being closed due to inactivity.

These directives allow users to customize their SSH client behavior for specific hosts or globally. By configuring SSH options in the SSH configuration file, users can streamline their SSH connections and enhance security and convenience.



---

## Note to Self

!!! note "git push branch to remote"

    To push only a specific branch to a remote repository in Git, you would use the following command:

    ```bash title="bash"
    git push <remote_name> <branch_name>
    ```

    Here's a breakdown:

    - `<remote_name>:` This is the name of the `remote` repository you want to push the branch to. For example, `origin` is the default name given to the remote repository you cloned from.
    - `<branch_name>:` This is the name of the branch you want to push to the `remote` repository.

    For example, if you want to push the branch named `my_branch` to the origin remote, you would use:
    

    ```bash title="bash"
    git push origin my_branch
    ```

    This command pushes only the `my_branch branch` to the origin remote repository.

    Make sure you have committed your changes to the branch before pushing it to the remote repository. If the branch doesn't exist on the remote repository, this command will create the branch on the remote repository and push the changes to it.

---

## Reference

- [git log graph](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-to-use-the-git-log-graph-command)
- [pretty graph dog](https://stackoverflow.com/questions/1057564/pretty-git-branch-graphs)
- [Git Bisect | How to use Git Bisect: video](https://www.youtube.com/watch?v=z-AkSXDqodc&ab_channel=GitKraken)

- [mkdocs plugins](https://github.com/mkdocs/catalog)

- [git tags? how to use them](https://www.bitband.com/blog/git-tags-are-they-useful-and-how-to-use-them/)