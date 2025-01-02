## Overview

Pre-commit hooks are automated scripts that are run before a commit is finalized in a version control system like Git. These hooks are designed to ensure that certain conditions or checks are met before the commit is actually made, helping to enforce code quality, maintain consistency, and prevent common issues. They can be used to run tests, linters, formatters, or any other checks that you want to happen before changes are committed to the repository.

**Common Use Cases for Pre-commit Hooks:**

1.  **Code Formatting**: Automatically format code to ensure consistency (e.g., using tools like [black](#) for Python, [prettier](#) for JavaScript, etc.).
2.  **Linting**: Check for code style issues or potential errors (e.g., using [eslint](#) or [flake8](#)).
3.  **Running Unit Tests**: Make sure that unit tests pass before code is committed.
4.  **Preventing Large Files**: Ensure that large files or sensitive data like passwords don't accidentally get committed.
5.  **Spell Checking**: Check for common spelling mistakes in commit messages or code.

**How It Works:**

- Pre-commit hooks are usually configured through a file called `.pre-commit-config.yaml`, which specifies the scripts or tools to run before each commit.
- The `pre-commit` framework (a tool that makes managing pre-commit hooks easier) is often used to configure and install these hooks.

**Steps to Set Up Pre-commit Hooks:**

1.  Install the `pre-commit` package:

    ```bash
    pip install pre-commit
    ```

2.  Create a `.pre-commit-config.yaml` file in the root of your repository. This file contains a list of hooks you want to run. Example `.pre-commit-config.yaml`:

    ```yaml
    - repo: https://github.com/pre-commit/mirrors-eslint
      rev: v7.32.0
      hooks:
        - id: eslint
          files: \.js$
    - repo: https://github.com/pre-commit/mirrors-black
      rev: 22.3.0
      hooks:
        - id: black
          language_version: python3
    ```

3.  Install the hooks:

    ```bash
    pre-commit install
    ```

4.  Run the hooks (either manually or they will run automatically when you commit):

    ```bash
    pre-commit run --all-files
    ```

**Advantages:**

- Code Consistency: Automatically ensures that everyone on the team follows the same coding standards.
- Prevents Common Mistakes: Helps catch issues before they are committed.
- Speeds Up Development: Automated checks can catch problems early, reducing the need for manual code review and fixing issues later.

**Example of Hook in Action:**

Suppose you have a `pre-commit` hook configured to run a linter before every commit. When you attempt to commit code, the linter will automatically run. If there are any issues (e.g., unused variables, missing semicolons, etc.), the commit will be blocked until the issues are fixed.

Overall, pre-commit hooks can help automate and enforce best practices, improving code quality and development efficiency.

---

!!! question "QUESTION"

---

### How to Install Pre-commit:

1.  **Install pre-commit using `pip`**: Since pre-commit is a Python tool, you install it with `pip` (Python's package manager):

    ```bash
    pip install pre-commit
    ```

    If you're using a `virtual environment` for Python, make sure to install [pre-commit](#) inside that environment.

2.  **Install `pre-commit` globally**: You can install pre-commit globally on your system to be able to use it in any project:

    ```bash
    pip install --user pre-commit
    ```

    This adds the pre-commit command to your terminal's path.

### Using `pre-commit` with JavaScript/TypeScript

Once pre-commit is installed, you configure it to run JavaScript/TypeScript-based hooks such as ESLint, Prettier, and TypeScript. The actual hooks themselves are configured via the `.pre-commit-config.yaml` file, which specifies the repositories and versions for each hook you want to use.

The core concept here is that pre-commit ==acts as a **hook manager**==, but it can run tools for any language, even though it is a Python-based utility.

### Alternative Installation Methods (without `pip`)

If you're hesitant about using Python or `pip`, there are alternative ways to set up pre-commit hooks, but they all still ultimately rely on installing pre-commit as a dependency (either globally or in your project environment).

???+ example

    -   **Using Homebrew (macOS/Linux):**

        If you're on macOS or Linux, you can install pre-commit using Homebrew (if you have it installed):

        ```
        brew install pre-commit
        ```

    -   **Using Docker:**

        If you want to avoid installing Python dependencies locally, you could also run pre-commit in a Docker container. This approach would involve setting up the `pre-commit` tool within a Docker environment, but it's generally not necessary unless you're specifically trying to avoid local installations.

### Why Use Pre-commit in JavaScript/TypeScript Projects?

The reason for using pre-commit in a JavaScript or TypeScript project, despite it being a Python tool, is that it makes it much easier to manage and automate common checks before committing code to a Git repository. These checks might include running linters, formatters, type-checking, and other hooks that are language-specific.

???+ tip "In summary:"

    -   Yes, `pre-commit` is installed via Python's `pip`, but it can manage hooks for a variety of programming languages.
    -   Once installed, you configure it via a `.pre-commit-config.yaml` file and it will run language-specific tools like ESLint, Prettier, and TypeScript in your React TypeScript project.

---

## Reference

- [Pre commit](https://pre-commit.com/)
- [How to Set Up Pre-Commit Hooks](https://stefaniemolin.com/articles/devx/pre-commit/setup-guide/)
- [Blog-bishowtheitguy](https://bishowtheitguy.github.io/blog/2024/07/10/pre-commit/)
