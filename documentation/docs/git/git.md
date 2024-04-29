# Git

```bash title="bash"
$ mkdir ~/my_website
$ cd ~/my_website

# the option -b followed by a default branch named main
$ git init -b main

# or you can intialize empty repo and add files later
$ git init -b main ~/my_website
$ cd ~/my_website
$ echo 'My awesome website!' > index.html
```

The `git init` command creates a hidden directory called ==.git== at the root level of your project. All revision information along with supporting metadata and Git extensions are stored in this top-level, hidden .git folder.


## Configuration Files

Git configuration files are all simple text files in the style of ==.ini== files. The configuration files are used to store preferences and settings used by multiple git commands.

Hierarchy of configuration files

-   **`.git/config`**

    ==Repository-specific== configuration settings manipulated with the `--file` option or by default. You can also write to this file with the `--local` option. These settings have the highest precedence.

-   **`~/.gitconfig`**

    ==User-specific== configuration settings manipulated with the `--global` option.

-   **`/etc/gitconfig`**

    ==System-wide== configuration settings manipulated with the `--system` option if you have proper Unix file write permissions on the gitconfig file. These settings have the lowest precedence. Depending on your installation, the system settings file might be somewhere else (perhaps in `/usr/local/etc` gitconfig) or may be absent entirely.

---

## Notes

```
# opens a git .config file

$ git config --global -e
```

---

## git divergent branches issue

```bash
git pull origin main --rebase
```

---

## git blame `command`
## git grep `command`

---

## Reference

- [Version Control with Git 3rd edition by Prem Kumar Ponuthorai & Jon Loeliger](https://www.amazon.com/Version-Control-Git-Collaborative-Development/dp/1492091197)


Solved

- [git divergent branches and need to specify how to reconcile them](https://ioflood.com/blog/solved-git-error-you-have-divergent-branches-and-need-to-specify-how-to-reconcile-them/)
- [Git Error: You have divergent branches and need to specify how to reconcile them.](https://medium.com/@rajlaxmii/git-error-you-have-divergent-branches-and-need-to-specify-how-to-reconcile-them-75e97bd8abd2)
- [Pulling without specifying how to reconcile divergent branches is discouraged](https://stackoverflow.com/questions/62653114/how-can-i-deal-with-this-git-warning-pulling-without-specifying-how-to-reconci)