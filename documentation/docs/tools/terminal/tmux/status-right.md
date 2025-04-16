# Status Right

To avoid overlap:

- Ensure you add clear separators (like spaces, pipes `|`, or other characters) between the battery status and Pomodoro icon in your `status-right` or `status-left` configuration.
- Adjust the `status-right-length` option to allocate enough space for all elements.
- Use format strings carefully to prevent elements from running into each other.

```bash title="~/.tmux.conf"
set -g status-right-length 150
set -g status-right 'Pomodoro: #{pomodoro_icon} | Batt: #{battery_icon} #{battery_percentage} | %H:%M'
```

This adds a pipe separator and enough length to prevent overlap.

If you use plugins like [tmux-battery](#) and [tmux-pomodoro-plus](#), make sure their output strings are separated and the status bar is wide enough.

In summary, battery status and Pomodoro icon can overlap if not spaced properly in the tmux status bar; adding separators and increasing status bar length prevents this issue

---

```
set -g status-right-length 150
set -g status-right 'Pomodoro: #{pomodoro_icon} | Batt: #{battery_icon} #{battery_percentage} | %I:%M %p'
```

```bash
# for audio play
sudo apt install mpv

mpv <audio-name>
```

---

## Reference

- [tmux-battery](https://github.com/tmux-plugins/tmux-battery)
- [tmux-pomodoro-plus](https://github.com/olimorris/tmux-pomodoro-plus)
