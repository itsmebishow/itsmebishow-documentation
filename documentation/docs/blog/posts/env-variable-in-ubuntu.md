---
draft: false
tags: [Python, Ubuntu]
comments: true
date: 2024-04-19
authors:
  - bishow
---

Understanding and manipulating environment variables is crucial for configuring your Ubuntu system to suit your needs. Environment variables are dynamic values that affect the behavior of processes running in your Linux environment. In this short guide, we'll explore how to `view`, `set`, and `manage` environment variables in Ubuntu.

<!-- more -->


## Viewing Environment Variables:

To see the environment variables currently set in your Ubuntu system, you can use the **printenv** command in the terminal. This command displays a list of all environment variables and their values.

!!! tip "bash"

    ```bash
    printenv

    printenv VARIABLE_NAME

    printenv PATH
    ```


## Setting Environment Variables:

Setting environment variables is done using the export command followed by the variable name and its value. For instance, **export MY_VAR=hello** sets the variable `MY_VAR` to the value hello. This change applies only to the current terminal session.

!!! tip "bash"

    ```
    # syntax
    export VARIABLE_NAME=value

    # example
    export MY_VAR=hello
    ```


## Persisting Environment Variables:

To make environment variables persistent across terminal sessions, you can add the **export** command to your shell configuration file (e.g., **.bashrc** or **.profile**). Editing this file allows you to set environment variables that will be loaded every time you start a new terminal session, ensuring consistency in your environment.

!!! tip "bash"

    ```
    nano ~/.bashrc
    ```

Then add the line:

!!! tip "bash"

    ```
    export MY_VAR=hello
    ```

Save the file and exit the editor. Now, the `MY_VAR` variable will be set to `hello` every time you open a new terminal session.

??? abstract "difference between bashrc & profile"

    The main difference between .bashrc and .profile is the timing of when they are executed:"

    === ".bashrc"

        - Executes each time a new interactive Bash shell is started.
        - Typically used for configuring the Bash shell environment for interactive use, such as setting aliases, defining shell functions, and customizing the prompt.


    === ".profile"
    
        - Executes once when a user logs in to their session.
        - Used for setting environment variables and executing commands that should apply to the entire session, including both interactive and non-interactive shells.
    
    ==In summary==, `.bashrc` is specific to the Bash shell and runs each time a new shell is opened, while `.profile` is more general and executes once per login session, affecting all processes started during that session.

    ---

    In Bash, when you use the export command to set an environment variable, you can either enclose the value in double quotes (") or omit the quotes entirely, ==as long as the value itself does not contain== any special characters or spaces.

    So both of these are valid:

    ```bash
    export FAVORITE_COLOR="blue"
    ```

    ```bash
    export FAVORITE_COLOR=blue
    ```

    Both commands will set the **FAVORITE_COLOR** environment variable to the string "blue". However, using double quotes allows you to include special characters or spaces in the value, while omitting quotes is simpler and works fine for simple values like "blue".



## Conclusion:

Mastering environment variables in Ubuntu empowers you to customize your system according to your preferences and requirements. Whether you're configuring paths, defining default settings, or integrating software components, understanding how to `view`, `set`, and `persist` environment variables is an essential skill for efficient Linux administration and development. With these simple commands, you can take full control of your Ubuntu environment, tailoring it to suit your needs effortlessly.

---
