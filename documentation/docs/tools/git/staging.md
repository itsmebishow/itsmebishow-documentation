# Git Staging

![Staging Area](https://git-scm.com/images/about/index1@2x.png){ width="300" }

The **staging area** (also called the **index**) is an intermediary area where Git holds changes that are going to be committed. It's like a preparation zone for your next commit. When you make changes to files, those changes are not automatically added to your Git repository. You have to add them to the staging area first using the `git add` command. Once they are staged, they are ready to be committed to the repository with `git commit`.

???+ tip "Key Concepts"

    -   **Unstaged changes**: Modifications in your working directory that haven’t been added to the staging area.
    -   **Staged changes**: Modifications that have been added to the staging area and are ready to be committed.

---

## [Three-Tiered Architecture of Git](https://tecadmin.net/git-staging-area-explained/)

![Staging Area in Git](https://media.licdn.com/dms/image/v2/D4D12AQHZ9ujcbU-ZzQ/article-cover_image-shrink_423_752/article-cover_image-shrink_423_752/0/1691171379537?e=1744243200&v=beta&t=akB3oyl3aP_Gv9nT-k0Xc1BibX9OfaJvAthrJlhKwt4){ width="300" }

![Understand Staging Area in Git’s Workflow](https://tecadmin.net/wp-content/uploads/2023/05/explained-git-staging-area.png){ width="300" }

---

## To See the Staging Area (Index) with Git Commands

1.  **Check which files are staged**: You can see the files that are currently staged for the next commit using:

    ```bash
    git ls-files --cached
    ```

    This will list all files that are in the staging area.

2.  **View the differences between your working directory and the staging area**: If you want to see the changes you've made that are staged, you can run:

    ```bash
    git diff --cached
    ```

    This will show you the differences between the staged files and the last commit.

3.  **Check the status of the working directory and staging area**: If you just want a general overview of what's staged and what's not, you can use:

    ```bash
    git status
    ```

    ???+ quote "This will show"

        -   ==Changes that are staged== (ready to be committed).
        -   ==Changes that **are not** staged== (i.e., modifications that are still in your working directory).

4.  **Inspect the contents of the staging area**: If you want a more detailed, lower-level view of what’s in the staging area, you can use:

    ```bash
    git diff --staged
    ```

    This will show the exact changes in the files that are staged for commit, in a diff format.

![https://softwaretechnologymq.github.io/research_mini_console/changing_code.html](https://softwaretechnologymq.github.io/research_mini_console/figs/git-workflow.jpg)

![git commit](https://codingnomads.com/images/a9cf95f8-f17b-43de-91c0-f75e1e14cd00/public)

## Why the Staging Area is Useful

- **Control over commits**: The staging area allows you to control exactly what changes will be included in your next commit. You can stage individual files or even specific parts of a file.
- **Multiple changes**: It lets you prepare multiple changes at once, even if they are made to different files, and commit them together in one cohesive commit.

![Git for IT Professionals](https://powershellmagazine.com/images/git312.png)

---

## Reference

- [Official: About - Staging Area](https://git-scm.com/about/staging-area)
- [Linkedin: Staging Area in Git: A Bridge between Working Directory and Repository](https://www.linkedin.com/pulse/staging-area-git-bridge-between-working-directory-repository/)
- [The Three-Tiered Architecture of Git](https://tecadmin.net/git-staging-area-explained/)
- [Changing Code](https://softwaretechnologymq.github.io/research_mini_console/changing_code.html)
- [git commit](https://codingnomads.com/git-commit)
- [Git for IT Professionals: Life Cycle of Repository Files](https://powershellmagazine.com/2015/07/27/git-for-it-professionals-life-cycle-of-repository-files-2/)
