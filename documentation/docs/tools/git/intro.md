![This is git logo](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e0/Git-logo.svg/512px-Git-logo.svg.png){ width="200" }

???+ success "Merge vs. Rebase"

    -   **Merge**: Creates a merge commit and preserves the history of both branches.
    -   **Rebase**: Rewrites history by applying your branch’s changes on top of another branch, resulting in a cleaner, linear history.

???+ tip "Rebase vs Merge"

    -   **Rebase**: ==Rewrites== history, no merge commit, linear history.
    -   **Merge**: ==Preserves== history as is, creates a merge commit, and ==is non-destructive==.

| **Aspect**                     | **Git Merge**                                                         | **Git Rebase**                                                                     |
| ------------------------------ | --------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Commit History**             | Keeps a **branching history** with merge commits.                     | Rewrites history, creating a **linear history**.                                   |
| **Collaboration**              | Safe for **collaborative workflows**. Merge commits maintain context. | Best for **solo developers or feature branches** before sharing.                   |
| **Conflict Resolution**        | Conflicts are resolved during the merge process.                      | Conflicts must be resolved **while rebasing**.                                     |
| **History Rewriting**          | Does not rewrite history.                                             | Rewrites history, so use with caution on **public/shared branches**.               |
| **Merge Commits**              | Creates a **merge commit**, marking the merge point.                  | **No merge commits** (unless resolving conflicts).                                 |
| **Use Case**                   | Ideal for merging long-running branches like `main` or `develop`.     | Ideal for **feature branches** or when preparing clean history for a pull request. |
| **Visibility of Merge Points** | Makes it clear when and where branches were merged.                   | No explicit record of where the merge happened.                                    |

???+ note "Subcategories in Git"

    Both `merge` and `rebase` fall under the **Branching and Merging** category, which can be broken down further into:

    1.  **Creating and Switching Branches**: (`git branch`, `git checkout`, `git switch`)
    2.  **Merging Branches**: (`git merge`, `git rebase`)
    3.  **Handling Merge Conflicts**: (`git mergetool`, manual conflict resolution)
    4.  **History Management**: (`git log`, `git reflog`, `git reset`)

    So, the general category is:

    -   **Branching and Merging** → `Merge` and `Rebase` are tools within this category.

---

## 🔥 Crucial and Commonly Used Git Topics in Daily Workflow:

Here are the most crucial and commonly used intermediate and advanced Git topics in real-time organizational environments:

1.  **Git Rebase**

    - Frequently used to keep a clean and linear commit history, especially when working with feature branches and integrating updates from the main branch.

2.  **Git Merge Conflicts**

    - Resolving merge conflicts is an essential skill when collaborating in teams. Conflicts happen often, and knowing how to resolve them is critical.

3.  **Git Stash**

    - Essential for temporarily saving uncommitted changes when you need to switch context or work on a different task without committing incomplete work.

4.  **Git Cherry-Pick**

    - Often used to apply specific changes from one branch to another without merging the entire branch, useful in bug fixes or hotfixes.

5.  **Git Reflog**

    - Critical for recovering lost commits or finding changes that were accidentally discarded or lost during rebase or reset.

6.  **Git Submodules**

    - Common in organizations that manage large, multi-repository projects or integrate dependencies between repositories.

7.  **Git Tagging**

    - Used for marking release points, especially in production workflows and versioning.

8.  **Interactive Rebase**

    - Very useful for cleaning up commit history before pushing to shared repositories or preparing pull requests.

9.  **Git Hooks**

    - Automation of workflows, such as running tests or formatting checks before committing or pushing code, is crucial for maintaining code quality.

10. **Git Remote Repositories and Configuration**

    - Working with multiple remotes, pushing changes to the correct remote, and handling repository configurations in collaborative projects.

These topics are heavily used in day-to-day development tasks, collaboration with team members, and managing repositories in an organization.

---

## 🛠️ Intermediate Git Topics:

Here are some intermediate and advanced Git topics that you can explore besides Git submodules:

1.  **Git Rebase**

    - Understand how to rewrite commit history and reapply commits on top of another branch.
    - Resolving conflicts during rebase.

2.  **Git Cherry-Pick**

    - Apply specific commits from another branch without merging the entire branch.

3.  **Git Stash**

    - Temporarily save changes that are not yet committed and apply them later.
    - Work with stash list, apply, and drop commands.

4.  **Git Reflog**

    - View the history of changes made to the HEAD and recover lost commits.

5.  **Git Merge Conflicts**

    - How to resolve conflicts during a merge.
    - Using tools like `git mergetool` and manual resolution.

6.  **Git Hooks**

    - Automate tasks at different points in the Git workflow (e.g., `pre-commit`, `post-merge`).

7.  **Git Tagging**

    - Create lightweight and annotated tags.
    - Manage release versions using tags.

8.  **Interactive Rebase**

    - Modify commits (e.g., squash, edit, reorder) during an interactive rebase session.

9.  **Git Subtree**

    - An alternative to submodules that can be simpler to manage for integrating multiple repositories.

10. **Git Bisect**

    - A binary search to find the commit that introduced a bug.

---

## ⚡ Advanced Git Topics:

1.  **Git Worktrees**

    - Manage multiple working directories from a single Git repository, useful for working on multiple branches at the same time.

2.  **Git Hooks in CI/CD**

    - Integrate Git hooks with continuous integration and continuous delivery pipelines.

3.  **Git Remote Repositories and Configuration**

    - Work with multiple remotes, add, remove, and push changes to different remotes.
    - Managing Git remotes and their URL configurations.

4.  **Git Submodules Advanced Use Cases**

    - Nested submodules, handling submodule updates, and cloning repos with submodules.

5.  **Git Filter-Branch / BFG Repo-Cleaner**

    - Rewrite Git history, remove sensitive data from commits, or clean large files from your history.
    - `git filter-branch` vs `BFG Repo-Cleaner` for history rewriting.

6.  **Git LFS (Large File Storage)**

    - Manage large files like images, audio, and video in Git repositories using Git LFS.

7.  **Git Notes**

    - Attach additional information to commits that doesn't affect the commit history.

8.  **Git Hooks in GitLab, GitHub, and Bitbucket**

    - Setting up and managing custom hooks in remote Git repositories and platforms.

9.  **Rewriting History with `git commit --amend` and `git reset`**

    - Safely modifying past commits, undoing commits, and fixing mistakes in the history.

10. **Distributed Workflows**

    - Learn how to work in distributed teams with different Git workflows: centralized, feature branching, Git flow, GitHub flow, etc.

---

## 💡 Bonus: Git Performance Tuning

- Optimize large repositories for better performance, reduce repository size, and improve speed when working with large datasets.

---

[Subscribe to our newsletter](http://bishowthapa.com.np){ .md-button .md-button--primary }

---

## Reference

- [Merging vs. rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)
- [Git Rebase vs. Merge: Enhance Your Code Workflow Now](https://www.simplilearn.com/git-rebase-vs-merge-article)
