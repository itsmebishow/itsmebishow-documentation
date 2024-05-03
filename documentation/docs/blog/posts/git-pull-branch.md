---
draft: false
comments: true
date: 2024-01-15
authors:
  - bishow
tags: [Programming]
---

# How to pull all branches from a remote repository in GitHub ?

`git fetch --all` command fetches all branches from the remote repository without merging them into your local branches.

<!-- more -->

To pull all branches from a remote repository in GitHub, you can follow these steps:

1.  Clone the Repository:

    If you haven't already cloned the repository, start by cloning it using the following command:

    ```bash title="bash"
    git clone <repository_url>
    ```

    Replace `<repository_url>` with the actual URL of the GitHub repository.

2.  Navigate to the Repository Directory:

    Change into the repository directory:

    ```bash title="bash"
    cd <repository_directory>
    ```

    Replace `<repository_directory>` with the name of the local directory where the repository was cloned.

3.  Fetch All Branches:

    Use the following command to fetch all branches from the remote repository:

    ```bash title="bash"
    git fetch --all
    ```

    This command fetches all branches from the remote repository without merging them into your local branches.

4.  Checkout Each Branch:

    To have a local copy of all branches, you need to check out each branch. You can iterate through all remote branches and create local tracking branches for them:

    ```bash title="bash"
    git branch -a | grep remotes/origin | grep -v HEAD | sed 's#^.*remotes/origin/##' | xargs -I {} git checkout -b {}
    ```

    This command lists all remote branches, filters out the HEAD branch, and creates a local branch for each remote branch.

Now, your local repository should have all branches from the remote GitHub repository. Keep in mind that this approach creates local branches that track the remote branches, so you can easily switch between them using `git checkout`.

---
