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
