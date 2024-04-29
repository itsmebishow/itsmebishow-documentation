tmux is short for [==t==]erminal [==mu==]ltiple[==x==]er. A multiplexer is simply a fancy way of describing an application that lets you easily manage multiple terminal windows within
one screen.

tmux runs a server/client architecture.

```bash title="bash"
# tmux prefix command
<Ctrl> and b
```

!!! success

    If you haven't specified a session name explicitly, Tmux will assign a `default name` to the session.

    The default session name typically consists of a numerical value, starting from `0` and incrementing for each new session

    ```bash title="bash"
    tmux
    ```


!!! tip "Getting Help with tmux by Reviewing Keyboard Shortcuts"

    ```
    Prefix + ?

    # listing all tmux session
    $ tmux list-sessions

    # shorcurt
    $ tmux ls

    # To resize the pane
    <Prefix>, arrow down (hold)
    ```


![https://thevaluable.dev/tmux-config-mouseless/](../assets/tmux-working-diagram.png)

## Installation

!!! example

    ```bash title="bash"
    $ sudo apt install tmux
    ```

## Sessions, Windows, Panes

!!! info

    === "Sessions"

        ```bash title="bash"
        # To list all sessions (from outside tmux)
        $ tmux ls

        # To create new session
        $ tmux new-session -s work

        # To detach the session: (d for detach)
        <Prefix>, d

        # To rename a session
        $ tmux rename-session -t  old_name  new_name

        # To select a session
        :choose-session

        # Move to next session
        <P>, (

        # Move to previous session
        <P>, )

        # To kill a session
        # You can type exit within a session to destroy the session
        exit
        #or
        ​tmux​ ​kill-session ​ ​-t​ ​ basic ​
        tmux​ ​kill-session ​ ​-t​ ​ second_session

        # Kill the tmux server and, as a result, every session
        $ tmux kill-server​
        ```

    === "Windows"

        ```bash title="bash"
        # To create new window: (c for create)
        <Prefix>, c

        # To rename a window
        <Prefix> ,

        # To move between windows
        # By default, windows in tmux each have a number, starting at 0
        <Prefix>, 0
        <Prefix>, 1

        # To find a window 
        <Prefix>, f

        # To display a visual menu of your windows 
        <Prefix>, w

        # To close a window
        type exit
        # or
        <Prefix>, &
        ```

    === "Panes"

        ```bash title="bash"
        # To split the window vertically
        <Prefix>, %

        # To split the pane horizontally
        # <Prefix>, "

        # To kill pane
        <Prefix>, x

        # To zoom the pane
        <Prefix>, z

        # To move the cursor to the pane to the right, left, down, or up
        <Prefix> and the right arrow key,
        <Prefix> and the left arrow key,
        <Prefix> and the down arrow key,
        <Prefix> and the up arrow key

        # Pane Layouts
        # To cycle through these layouts by pressing <PREFIX> SPACEBAR 
        <PREFIX> SPACEBAR 
        ```

---

## Manipulating Text

!!! note

    There are **two important components of tmux**

    - Copy mode
    - paste buffers

    === "**Explaining the Window history**"

        In order to work its magic and keep everything in a single terminal window, tmux
        has to hide all of the text that won't fit in the currently viewed pane. It keeps all of
        this text stored in something called ==Window history==.

        ```
        # copy mode
        # To enter copy mode
        <Prefix>, [

        # To copy text into the paste buffer. 
        # This sets the start point of the selection.

        press Ctrl + Space bar (Space bar)

        # When you are satisfied with your selection,
        simply press Meta + w (Enter) 
        # to copythe text and you will leave Copy mode immediately
        ```

        Interacting with the paste buffer

        The paste buffer is a holding bucket for all of the text you will copy. It is actually a stack, so each item copied from Copy mode is added at the top of the stack.


    === "**paste buffer**"

        ```
        # Pasting text from the paste buffer
        <Prefix>, ]

        # Choosing items from the paste buffer
        <Prefix>, =
        ```

## Tmux Modes

!!! tip "Explaining the different tmux modes"

    1.   **Default** mode:

         You are in `Default mode` ==by default==, and if you go into any other mode and then exit it, you'll end up back in Default mode.

    2.   **Copy** mode:

        This allows us to access the ==Window history== and `copy/paste` contents from that history.

    3.   **Command** mode:

        This mode is used to enter arbitrary tmux commands. It is similar to the vi mode of the same name and can be accessed by `<Prefix>, :`.

    4.   **Clock** mode:

        This mode shows the current time and is more of a novelty utility than an actual mode, like the rest. It can be accessed by `<Prefix>, t`.

    5.   **Control** mode:

        This mode allows third-party applications to interact with tmux through a text-only protocol.


---

## tmux `source-file`

!!! example

    === "Usage"

        `source-file`: Loads and executes commands from a file within the current Tmux session.

        ```bash title="bash"
        tmux source-file <file_path>
        ```

        When you run `tmux source-file <file_path>`, Tmux reads the commands from the specified file and executes them as if they were entered directly into the Tmux command prompt.

    === "Theory"

        The `tmux` command is used to interact with a running Tmux session. **source-file** is an ==argument== you can pass to tmux to execute commands from a specified file within the context of the current Tmux session.

        You might use tmux source-file in the following scenarios:

        - **Reloading Tmux configuration:** If you've made changes to your Tmux configuration file (`~/.tmux.conf` by default) and want to apply those changes to the current Tmux session without restarting it, you can use `tmux source-file ~/.tmux.conf`.

        - **Executing a series of commands:** If you have a set of Tmux commands stored in a file and want to execute them together, you can use `tmux source-file <file_path>` to run them in sequence.

        - **Automating tasks:** You can use `tmux source-file` within scripts or automation tools to apply Tmux configurations or perform actions programmatically.

        Remember, `tmux source-file` is used to execute Tmux commands stored in a file, and it's typically used to apply configurations or perform actions within an existing Tmux session.

---

## - Shorcuts `alias`

!!! question

    ```bash title="bash"
    ​$ tmux​ ​list-sessions
    # alias
    $ ​tmux​ ​ls 

    ​$ tmux​ ​new-session ​ ​-s ​ ​basic​
    # alias
    $ ​tmux​ ​new​ ​-s ​ ​basic

    # By using the -n flag, we tell tmux to name the first window so we can identify it easily.
    ​$ tmux​ ​new​ ​-s ​ ​windows ​ ​-n ​ ​shell 

    $ tmux rename-session -t old_name new_name
    # alias
    $ tmux rename -t old_name new_name.​
    ```

---

## - Easter Eggs

!!! question

    ```bash title="bash"

    # To display clock on the screen.
    <Prefix>, t


    # list of sessions and select any of them.
    <Prefix>, s 

    # To attach last session, after you detach session
    $ tmux attach

    # display tmux keyboard shortcuts
    <Prefix>, ?
    ```

---

## - Commands

Default Commands for `Sessions`, `Windows`, and `Panes`

!!! abstract

    === "Sessions Commands"

        ```
        Prefix + (	Switch to the previous session
        Prefix + )	Switch to the next session
        Prefix + s	Display an interactive session list
        Prefix + d	detach from the current session
        Prefix + $	rename a session in tmux
        Prefix + L	Select the most recently used session (or the last session).

        # List all available sessions
        tmux ls

        # Destroy all sessions and kill all processes
        tmux kill-server
        ```

    === "Windows Commands"

        ```
        Prefix + c	Create a new window
        Prefix + p	Switch to the previous window
        Prefix + n	Switch to the next window

        Prefix + 0-9	Switch to a window using it’s index number

        Prefix + w	Choose a window from an interactive list

        Prefix + &	Force kill-all processes in an unresponsive window
        Prefix + %	Split windows horizontally
        Prefix + “	Split windows vertically

        exit	Close a window

        ---

        <Prefix>, n: Moves to the next window.
        <Prefix>, p: Moves to the previous window.

        <Prefix>, 0 ... 9:Selects windows by number.

        <Prefix>, w: Displays a selectable list of windows in the current session.
        <Prefix>, &: Closes the current window after prompting for confirmation.

        <Prefix>, q: Momentarily displays pane numbers in each pane.
        <Preix>, x: Closes the current pane after prompting for confirmation.

        <Prefix>, space: Cycles through the various pane layouts.
        ```


---

![https://www.rffuste.com/2023/04/17/oh-my-tmux-mapheet/](../assets/tmux-cheatsheet.png)

## - tmux command mode

!!! note

    tmux `command` mode:

    In tmux, ==command mode== allows you to interact with tmux commands without prefixing them with the tmux prefix key (by default, it's `Ctrl+b`). This can be convenient for executing a series of tmux commands quickly.

    To enter command mode in tmux, you can use the tmux prompt key, which is `:` (colon) by default. Pressing this key will bring up the tmux command prompt at the bottom of the terminal window.

    Here's how you can use command mode:

    - Press ==Ctrl+b== (default prefix key) to enter tmux command mode.
    - Type ==:== (colon). This will bring up the tmux command prompt at the bottom of the terminal window.
    - Enter the tmux command you want to execute, for example, `split-window` to split the current window.
    - Press Enter to execute the command.

    ```sh
    # Create a new window
    :new-window

    # Split the current window into multiple panes.
    :split-window

    # Split the current window into panes horizontally.
    :split-window -h

    # Detach from the tmux session.
    :detach-client

    # List all tmux sessions.
    :list-sessions

    # Reload the tmux configuration file.
    :source-file ~/.tmux.confS
    ```

---

## Plugins


!!! example "tmux plugin manager: `tpm`"

      Installing: [Tmux Plugin Manager](https://github.com/tmux-plugins/tpm) - `TPM`

      ```ssh title="bash"
      git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
      ```

      ```sh
      # Here's how you can create a .tmux directory if you need it:
      mkdir ~/.tmux

      # To create a basic configuration file, you can do the following:
      touch ~/.tmux.conf
      ```

      - **One way**

          While in tmux session, press `prefix` + `I` (capital `i`, as in Install) to fetch the plugin.

          `Notes`: The default prefix to tmux is `Ctrl+b`.

      - **Other way**

          You can also reload the Tmux configuration file by running the following command to add the plugin.

          ```sh title="bash"
          tmux source ~/.tmux.conf
          ```

### tmux-resurrect

a plugin that allows to easily **save and restore tmux environment** ==after system restarts==.

!!! tip

    === "Usage"

        Default key bindings: 

        - ++"prefix"+"Ctrl-s"++ :  **save**
        - ++"prefix"+"Ctrl-r"++ :  **restore**

    === "Installation"

    Add plugin to the list of TPM plugins in `.tmux.conf`:

    ```conf
    set -g @plugin 'tmux-plugins/tmux-resurrect'
    ```

    Hit `prefix + I` to fetch the plugin and source it. You should now be able to use the plugin.


### tmux-continuum

a plugin that **automates the saving and restoring** of the tmux environment.

!!! tip

    === "Usage"

        **Continuous saving**

        Tmux environment will be saved at the interval of 15 minutes. All the saving happens in the background without the impact to your workflow. This action starts automatically when the plugin is installed.

        **Automatic tmux start**

        Tmux is automatically started after the computer/server is turned on.

        **Automatic restore**

        Last saved environment is automatically restored when tmux is started. To enable this, put the following in the `.tmux.conf`:

        ---

        ```conf title="tmux.conf"
        set -g @continuum-restore 'on'
        ```

    === "Installation"

        Installation with Tmux Plugin Manager (recommended)

        ==Please make sure you have `tmux-resurrect` installed==.

        Add plugin to the list of TPM plugins in `.tmux.conf`:

        ```conf title="tmux.conf"
        set -g @plugin 'tmux-plugins/tmux-resurrect'
        set -g @plugin 'tmux-plugins/tmux-continuum'
        ```

        Hit `prefix + I` to fetch the plugin and source it. The plugin will automatically start "working" in the background, no action required.



---

## Reference

- ==Site Reference==
- [tmux](https://www.linode.com/docs/guides/persistent-terminal-sessions-with-tmux/)

- ==Books==
- [Getting Started with tmux by Victor Quinn, J.D.](https://www.amazon.com/Getting-Started-tmux-Victor-Quinn-ebook/dp/B00NW474T6)
- [tmux Taster by Mark McDonnell](https://www.oreilly.com/library/view/tmux-taster/9781484207758/)
- [tmux 2: Productive Mouse-Free Development by Brian P. Hogan](https://pragprog.com/titles/bhtmux2/tmux-2/)


- ==Blog==
- [Installing TPM](https://ostechnix.com/install-tmux-plugin-manager/)
- [usefull tmux configuration](https://dev.to/iggredible/useful-tmux-configuration-examples-k3g)
- [customizing tmux configuration](https://hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/)
- [tmux config](https://www.hostinger.com/tutorials/tmux-config)
- [Useful Tmux Configuration](https://dev.to/iggredible/useful-tmux-configuration-examples-k3g)
- [Terminal Setup with Zsh + Tmux + Dracula Theme](https://dev.to/andrenbrandao/terminal-setup-with-zsh-tmux-dracula-theme-48lm)
- [Replicate My Tmux Setup in Less Than 5 Minutes [Beginner Friendly!]](https://www.youtube.com/watch?v=78FjNkrPn5Y)

- ==Github==
- [tmux plugins: github](https://github.com/tmux-plugins/tpm#installation)
- [list of awesome tmux: github](https://github.com/rothgar/awesome-tmux?tab=readme-ov-file#plugins)
- [dracula tmux plugins: github](https://github.com/dracula/tmux?tab=readme-ov-file)
- [draculatheme offical site](https://draculatheme.com/tmux)
- [EVERYTHING YOU NEED TO KNOW ABOUT TMUX – Reconstructing Tmux Sessions After Restarts](https://arcolinux.com/everything-you-need-to-know-about-tmux-reconstructing-tmux-sessions-after-restarts/)
- [Tmux/plugins/resurrect](https://wiki.gentoo.org/wiki/Tmux/plugins/resurrect)
- [tmux-continuum: github](https://github.com/tmux-plugins/tmux-continuum)

- ==Stackoverflow==
- [How to press Ctrl + b + capital I (trying to install plugins in tmux)?](https://unix.stackexchange.com/questions/744304/how-to-press-ctrl-b-capital-i-trying-to-install-plugins-in-tmux)
