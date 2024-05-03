---
drafts: false
date: 2024-04-26
tags: [Tmux]
comments: false
authors:
  - bishow
---

# Navigating Tmux: A Quick Guide to Swapping Windows

In Tmux, swapping windows means switching the positions of two windows within the same session. Here's how you can swap windows:

<!-- more -->

!!! note

    1. Enter Tmux command mode:
      
        Press **Ctrl** + **b** (the default prefix) followed by ==:==. You'll see a prompt at the bottom of the screen.

    2. Enter the swap-window command:

        Type swap-window -s `<source-index>` -t `<target-index>` and press Enter.

        - `<source-index>`: The index of the window you want to swap.
        - `<target-index>`: The index of the window you want to swap with.


        For example, if you want to swap the window at index `1` with the window at index `3`, you would type:

        ```bash title="bash"
        swap-window -s 1 -t 3
        ```

    3. Verify the swap:

        After executing the command, the positions of the windows will be swapped.

    ---

    This command can also be abbreviated as swapw for convenience:

    ```bash title="bash"
    :swapw -s <source-index> -t <target-index>
    ```

---

## Reference

