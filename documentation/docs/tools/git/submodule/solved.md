# Solved

The error message fatal: '`test-example.github.io`' already exists in the index occurs because the folder `test-example.github.io` is already tracked (staged) in Git's index, which prevents adding it again as a submodule at the same path.

## Why this happens:

- The directory you want to add as a `submodule` **is already present** and ==tracked== in your repository's ==index==.
- Git does not allow adding a `submodule` where files or folders with the same name already exist in the index.

---

## How to fix this:

1.  **Check what is currently in the index for that folder**:

    ```bash
    git ls-files --stage text-example.github.io
    ```

    This will show the files or submodule entries staged under that folder.

2.  **Remove the folder from the index (`unstage it`) without deleting the actual folder**:

    ```bash
    git rm --cached -r text-example.github.io
    ```

    This command removes the folder from the Git index but leaves the files in your working directory.

3.  **Now add the submodule again**:

    ```bash
    git submodule add <url_to_text-example.github.io_repo> text-example.github.io
    ```

4.  **Commit the changes**:

    ```bash
    git commit -m "Added text-example.github.io as a submodule"
    ```

???+ note "Additional notes"

    -   If the folder contains many files already staged, `git rm -r --cached` is necessary to unstage all of them.
    -   If you want to completely remove the folder and start fresh as a submodule, you can delete the folder manually before adding the submodule.
    -   After adding the submodule, Git will track it as a "gitlink" (special entry) rather than regular files.

This approach is confirmed by multiple sources addressing the same error with submodules, which recommend unstaging the existing folder before adding it as a submodule

---

## Reference

- [Issue with adding common code as git submodule: "already exists in the index" - Stackoveflow](https://stackoverflow.com/questions/12898278/issue-with-adding-common-code-as-git-submodule-already-exists-in-the-index)
- [Adding Git Submodules](https://zmhassan.gitbooks.io/reactjs-redux-patternfly-library/content/adding-git-submodules.html)
- [Official: Git Tools - Submodules](https://git-scm.com/book/id/v2/Git-Tools-Submodules)
