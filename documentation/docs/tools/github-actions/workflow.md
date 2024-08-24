
???+ abstract "Structure of a GitHub Actions Workflow"

    A GitHub Actions workflow YAML file consists of several key components:

    -   **Name**: The name of the workflow.
    -   **On**: Specifies the events that trigger the workflow.
    -   **Jobs**: Defines one or more jobs that the workflow will run.
    -   **Steps**: Specifies the individual steps to be executed within each job.

    ---

    Create a New Workflow:

    -   In the `.github/workflows` directory of your repository, create a new file (e.g., `ci.yml`, `test.yml`, or `build.yml`). If the `.github/workflows` directory does not exist, ==create it==.



---


Understanding the structure of a GitHub Actions workflow is key to effectively automating your software development processes. Here’s a detailed breakdown of each component in a GitHub Actions workflow YAML file:


1.  **Workflow Name**

    ```yaml title="yaml"
    name: CI
    ```

    -   Purpose: Provides a name for the workflow. This name will be visible in the GitHub Actions tab.
    -   Example: `CI` stands for Continuous Integration, but you can name it based on its function (e.g., `Deploy`, `Test Suite`).


2.  **Trigger Events**

    ```yaml title="yaml"
    on:
        push:
            branches:
                - main
        pull_request:
            branches:
                - main
    ```

    -   Purpose: Defines the events that trigger the workflow to run.
    -   Example: The workflow is triggered on `push` or `pull_request` events targeting the `main` branch.


3.  **Jobs**

    ```yaml title="yaml"
    jobs:
        build:
            runs-on: ubuntu-latest
    ```

    -   Purpose: Defines a collection of steps to be executed. Each job runs independently and can run in parallel or sequentially based on dependencies.
    -   Example: The job named `build` runs on the latest version of Ubuntu.


4.  **Steps**

    ```yaml title="yaml"
    steps:
        -   name: Checkout code
            uses: actions/checkout@v3
        -   name: Set up Node.js
            uses: actions/setup-node@v3
            with:
                node-version: '14'
        -   name: Install dependencies
            run: npm install
        -   name: Run tests
            run: npm test
    ```

    -   Purpose: Specifies the individual actions or commands to execute within a job.



5.  **Job Dependencies**

    ```yaml title="yaml"
    jobs:
        build:
            runs-on: ubuntu-latest

        deploy:
            runs-on: ubuntu-latest
            needs: build
    ```

    -   Purpose: Specifies dependencies between jobs, ensuring certain jobs run only after others have completed.
    -   `needs`: Lists jobs that must complete before this job starts.
    -   Example: The `deploy` job depends on the successful completion of the `build` job.



6.  **Secrets and Environment Variables**

    ```yaml title="yaml"
    jobs:
        deploy:
            runs-on: ubuntu-latest
            env:
                NODE_ENV: production
            steps:
                - name: Deploy
                run: ./deploy.sh
                env:
                    DEPLOY_TOKEN: ${{ secrets.DEPLOY_TOKEN }}
    ```

    -   Purpose: Manage sensitive information and configuration settings.
    -   Secrets: Accessed via `${{ secrets.SECRET_NAME }}`. They are stored securely and not exposed in logs.
    -   Environment Variables: Set using the `env` keyword at the job or step level.
    -   Example:
            -   Environment Variable: Sets `NODE_ENV` to `production`.
            -   Secret: Uses a deployment token stored as a secret.



7.  **Matrix Builds**

    ```yaml title="yaml"
    jobs:
        test:
            runs-on: ubuntu-latest
            strategy:
                matrix:
                    node-version: [12, 14, 16]
            steps:
                -   name: Checkout code
                    uses: actions/checkout@v3
                -   name: Set up Node.js
                    uses: actions/setup-node@v3
                    with:
                        node-version: ${{ matrix.node-version }}
                -   name: Run tests
                    run: npm test
    ```

    -   Purpose: Run multiple configurations of a job, such as different versions of Node.js.
    -   Example: Runs the tests with Node.js versions 12, 14, and 16.



8.  **Artifacts and Caching**

    ```yaml title="yaml"
    jobs:
        build:
            runs-on: ubuntu-latest
            steps:
            -   name: Cache Node.js modules
                uses: actions/cache@v3
                with:
                    path: ~/.npm
                    key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
                    restore-keys: |
                    ${{ runner.os }}-node-
            -   name: Build
                run: npm run build
    ```

    -   Purpose: Manage build artifacts and cache dependencies to speed up workflows.
    -   Caching: Saves and restores dependencies to reduce build times.
    -   Example: Caches Node.js modules to speed up dependency installation.



---


```yaml
# .github/workflows/python-app.yml
name: Python application

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Add deadsnakes PPA and install Python 3.8
        run: |
          sudo add-apt-repository ppa:deadsnakes/ppa
          sudo apt-get update
          sudo apt-get install -y python3.8 python3.8-venv python3.8-dev
          python3.8 -m pip install --upgrade pip
          python3.8 -m pip install pipenv

      - name: Verify Python and Pipenv installation
        run: |
          python3.8 --version
          pipenv --version

      - name: Install dependencies
        run: |
          pipenv --python python3.8 install --dev

      - name: Run tests
        run: |
          pipenv run pytest

```


