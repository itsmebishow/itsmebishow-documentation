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

- **`.git/config`**

  ==Repository-specific== configuration settings manipulated with the `--file` option or by default. You can also write to this file with the `--local` option. These settings have the highest precedence.

- **`~/.gitconfig`**

  ==User-specific== configuration settings manipulated with the `--global` option.

- **`/etc/gitconfig`**

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

To delete a branch on both your local repository and GitHub, you can follow these steps:

## Deleting Locally:

1.  Checkout a Different Branch:

    Before deleting the branch, ensure you're not currently on the branch you intend to delete. You can switch to another branch using:

    ```bash
    git checkout <different_branch>
    ```

2.  Delete the Branch: Use the following command to delete the branch locally:

    ```bash
    git branch -d <branch_name>
    ```

    If the branch has not been merged yet, you might need to use -D instead of -d to force delete.

## Deleting on GitHub:

3.  Push the Deletion: To delete the branch on GitHub, you need to push the deletion to the remote repository:

    ```bash
    git push origin --delete <branch_name>
    ```

    This command will delete the branch on GitHub (the origin remote).

To delete a branch on both your `local` repository and `GitHub`, you can follow these steps:

---

## Images

![https://dev.to/mollynem/git-github--workflow-fundamentals-5496](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fvpxeexqyfvf4hw3zxtbn.png)

![https://programming.earthonline.us/you-can-master-git-git-commands-with-these-diagrams-40a0b2f5cc42](https://miro.medium.com/v2/resize:fit:720/format:webp/1*eGdNATA_BGQcA1xUvc9Irg.png)

![https://cloudstudio.com.au/2021/06/26/git-command/](https://cloudstudio.com.au/wp-content/uploads/2021/06/GitWorkflow-4-768x495.png)

![https://blog.osteele.com/2008/05/my-git-workflow/](https://images.osteele.com/2008/git-transport.png)

![https://imgur.com/oodiCnB](https://i.imgur.com/oodiCnB.png)

- [Understanding the Git & Github Workflow ](https://jr0cket.co.uk/2013/08/getting-to-grips-with-git-understanding-the-simple-workflow.html.html)
- [Git workflow diagram: reddit](https://www.reddit.com/r/git/comments/99ul9f/git_workflow_diagram_showcasing_the_role_of/?rdt=41318)

**Workflow**

![https://nexuslinkservices.com/git-workflow-in-software-development-life-cycle/](https://nexuslinkservices.com/wp-content/uploads/2019/01/Git-1.jpg)

---

## Reference

- [Version Control with Git 3rd edition by Prem Kumar Ponuthorai & Jon Loeliger](https://www.amazon.com/Version-Control-Git-Collaborative-Development/dp/1492091197)
- Solved
- [git divergent branches and need to specify how to reconcile them](https://ioflood.com/blog/solved-git-error-you-have-divergent-branches-and-need-to-specify-how-to-reconcile-them/)
- [Git Error: You have divergent branches and need to specify how to reconcile them.](https://medium.com/@rajlaxmii/git-error-you-have-divergent-branches-and-need-to-specify-how-to-reconcile-them-75e97bd8abd2)
- [Pulling without specifying how to reconcile divergent branches is discouraged](https://stackoverflow.com/questions/62653114/how-can-i-deal-with-this-git-warning-pulling-without-specifying-how-to-reconci)
