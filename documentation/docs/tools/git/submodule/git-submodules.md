To add other repositories inside your **main GitHub repository**, there are ==two primary ways== you can do this:

1.  **Using Git Submodules** (if you want to maintain links to the original repos)
2.  **Copying the Code Directly** (if you want everything to be part of your main repo)

---

## ✅ Method 1: Using Git Submodules (Recommended for Linked Repos)

Git submodules allow you to keep other repositories as a part of your main repository without copying the code. This is useful when you want to keep track of changes in the original repo and update your submodule accordingly.

???+ tip "Steps to Add a Submodule"

    1.  **Go to your main repo directory**:

        ```bash title="bash"
        cd your-main-repo
        ```

    2.  **Add the other repo as a submodule**:

        ```bash title="bash"
        git submodule add https://github.com/username/other-repo.git path/to/submodule
        ```

        Example:

        ```bash title="bash"
        git submodule add https://github.com/your-org/utils.git utils
        ```

    3.  **Commit the changes**:

---

**🛠 Updating a Submodule:**

When the other repo gets updated, you can pull the latest changes to your main repo using:

```bash title="bash"
git submodule update --remote
```

---

## ✅ Method 2: Copying the Code from Other Repos (Simple Method)

If you don’t want to maintain a link to the original repo, you can simply copy the code into your main repo.

???+ tip "Steps"

    1.  Clone the other repo:

        ```bash title="bash"
        git clone https://github.com/username/other-repo.git
        ```

    2.  Copy the necessary files/folders to your main repo.


    3.  Commit and push the changes:s


        ```bash title="bash"
        cd your-main-repo
        git add .
        git commit -m "Added other repo code"
        git push
        ```

---

## ✅ Comparison Between Submodules and Copying:

| Feature                     | Git Submodule                     | Copy Code |
| --------------------------- | --------------------------------- | --------- |
| Keeps Link to Original Repo | ✅ Yes                            | ❌ No     |
| Easy to Update Code         | ✅ Yes                            | ❌ Manual |
| Can Customize Code          | ✅ Yes (but careful with updates) | ✅ Yes    |
| Easy to Setup               | ❌ Slightly Complex               | ✅ Easy   |

---

## 🔧 Common Git Submodule Commands:

| Command                               | Description                                  |
| ------------------------------------- | -------------------------------------------- |
| `git submodule add <repo-url> <path>` | Adds a submodule to your repository          |
| `git submodule update --remote`       | Updates all submodules to the latest version |
| `git submodule init`                  | Initializes the submodules in your project   |
| `git submodule status`                | Displays the current status of submodules    |
| `git submodule deinit <path>`         | Removes a submodule from your project        |

---

## Deleting Submodule

The majority of answers to this question are outdated, incomplete, or unnecessarily complex.

A submodule cloned using `git 1.7.8` or newer will leave at most four traces of itself in your local repo. The process for removing those four traces is given by the three commands below:

```bash
# Remove the submodule entry from .git/config
git submodule deinit -f path/to/submodule

# Remove the submodule directory from the superproject's .git/modules directory
rm -rf .git/modules/path/to/submodule

# also remove the .git/config links for submodule


# Remove the entry in .gitmodules and remove the submodule directory located at path/to/submodule
git rm -f path/to/submodule
```

???+ quote "Note by Bishow"

    1. deinit
    2. remove the submodule from  `.git/config` file, links of the submodule.
    3. `rm -rf .git/modules/<submodule_path>`: remove Submodule in the `git/modules` directory, removes the unnecessay module.
    4. `git rm <submodule>`.

    -   `git rm --cached <submodule_path>`: Remove the Submodule from the Git Index

???+ tip "Summary of Key Commands:"

    -   **Add a submodule**: `git submodule add <repository_url> <path>`
    -   **Initialize submodules**: `git submodule init`
    -   **Update submodules**: `git submodule update`
    -   **Clone with submodules**: `git clone --recurse-submodules <repository_url>`
    -   **Remove submodule**: `git submodule deinit <path> && git rm <path>`

- [Git Submodules: Adding, Using, Removing, Updating](https://chrisjean.com/git-submodules-adding-using-removing-and-updating/)
- [stackoverflow: ](https://stackoverflow.com/questions/1260748/how-do-i-remove-a-submodule/36593218#36593218)
- [gist: delete_git_submodule](https://gist.github.com/myusuf3/7f645819ded92bda6677)
- [geeksforgeeks: How to Remove a Submodule?](https://www.geeksforgeeks.org/how-to-remove-a-submodule/)
- [Submodules: Core concept, workflows and tips ](https://www.atlassian.com/git/articles/core-concept-workflows-and-tips)
