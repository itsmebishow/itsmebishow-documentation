# Common Issue

???+ bug

    ```bash
    $ git pull

    remote: Enumerating objects: 17, done.
    remote: Counting objects: 100% (17/17), done.
    remote: Compressing objects: 100% (3/3), done.
    remote: Total 9 (delta 6), reused 9 (delta 6), pack-reused 0 (from 0)
    Unpacking objects: 100% (9/9), 1.38 KiB | 6.00 KiB/s, done.

    From github.com:Test/documentation-github.io
        4ab15430..c8f26208  main       -> origin/main
    Fetching submodule Test.github.io
    fatal: remote error: upload-pack: not our ref fb4213ca8723fb3ca2777a7e14365169d1d5411e
    Errors during submodule fetch:
        Test.github.io
    ```

## Solved

???+ success

    ```bash
    $ git submodule update --init --recursive
    $ git submodule update --remote
    ```

---

## Submodule Commands

To fetch submodules in Git and ensure you have the latest changes from the submodule repositories, follow these steps:

1.  **Initialize submodules (if not done yet)**:

    If you have just cloned a repository with submodules, first initialize them:

    ```bash
    git submodule update --init --recursive
    ```

    This command initializes and fetches all submodules recursively, setting them up in your local repo.

2.  **Fetch latest changes for submodules**:

    To fetch the latest commits for all submodules from their remote repositories, use:

    ```bash
    git submodule update --remote
    ```

    This command goes into each submodule and fetches the latest changes from the branch the submodule is tracking.

3.  **Fetch recursively for nested submodules**:

    If your project contains nested submodules (submodules inside submodules), use recursive fetch:

    ```bash
    git fetch --recurse-submodules
    ```

    This fetches all new commits for the main project and all submodules at every level.

4.  **Update submodules after fetching**:

    After fetching, you may want to update the submodules to the latest commit on their tracked branches:

    ```bash
    git submodule update --remote --recursive
    ```

    This combines fetching and updating recursively for all submodules.

5.  **Automate submodule fetch on pull**:

    To make Git automatically fetch and update submodules when you pull the main repository, configure:

    ```bash
    git config --global submodule.recurse true
    ```

    This ensures submodules are updated along with the main repo when running git pull.

6.  **Manual fetch inside a submodule (optional)**:

    You can also enter the submodule directory and run:

    ```js
    git fetch
    git merge origin/<branch>
    ```

    to manually fetch and merge changes from the upstream branch.

Summary of useful commands for fetching submodules

| Command                                      | Purpose                                            |
| -------------------------------------------- | -------------------------------------------------- |
| `git submodule update --init --recursive`    | Initialize and fetch all submodules recursively    |
| `git submodule update --remote`              | Fetch latest commits for all submodules            |
| `git fetch --recurse-submodules`             | Fetch all commits recursively including submodules |
| `git submodule update --remote --recursive`  | Fetch and update all submodules recursively        |
| `git config --global submodule.recurse true` | Auto-update submodules on `git pull`               |

These commands ensure your submodules are up to date with their remote repositories and properly integrated into your main project.

- [How To Pull The Latest Git Submodule](https://phoenixnap.com/kb/git-pull-submodule)
- [Stackoverflow: Pull latest changes for all git submodules](https://stackoverflow.com/questions/1030169/pull-latest-changes-for-all-git-submodules)
- [How to fetch git submodules](https://graphite.dev/guides/git-fetch-submodules)
- [Git Tools - Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
- [How to Utilize Submodules within Git Repos](https://blog.bitsrc.io/how-to-utilize-submodules-within-git-repos-5dfdd1c62d09)
- [How to Use Git Submodules – Explained With Examples](https://www.freecodecamp.org/news/how-to-use-git-submodules/)
- [Submodules: Core concept, workflows and tips ](https://www.atlassian.com/git/articles/core-concept-workflows-and-tips)
- [Git Submodules: Adding, Using, Removing, Updating](https://chrisjean.com/git-submodules-adding-using-removing-and-updating/)
