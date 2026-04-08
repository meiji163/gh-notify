<div align="center">

# GitHub CLI Notification Extension
A [gh](https://github.com/cli/cli) extension to view your GitHub notifications from the command line.

https://github.com/meiji163/gh-notify/assets/92653266/b7d7fcdb-8a25-43fc-8f63-d11f30960084

 </div>

## Install

Make sure you have [GitHub CLI (gh)](https://github.com/cli/cli#installation) installed.

```sh
# install
gh ext install meiji163/gh-notify
# upgrade
gh ext upgrade meiji163/gh-notify
# uninstall
gh ext remove meiji163/gh-notify
```

To use `gh notify` interactively, install these tools as well:
- [Fuzzy Finder (fzf)](https://github.com/junegunn/fzf#installation) - This allows for
  interaction with listed data.
- [Python](https://www.python.org/) - In cases where `gh` can't open the `URL` in your browser, this
  one-liner is used as a cross-platform solution: `python -m webbrowser <URL>`

## Usage

```sh
gh notify [Flags]
```

| Flags    | Description                                             | Example                                              |
| -------- | ------------------------------------------------------- | ---------------------------------------------------- |
| <none>   | show all unread notifications                           | `gh notify`                                          |
| `-a`     | show all (read/ unread) notifications                   | `gh notify -a`                                       |
| `-e`     | exclude notifications matching a string (REGEX support) | `gh notify -e "MyJob"`                               |
| `-f`     | filter notifications matching a string (REGEX support)  | `gh notify -f "Repo"`                                |
| `-h`     | show the help page                                      | `gh notify -h`                                       |
| `-n NUM` | max number of notifications to show                     | `gh notify -an 10`                                   |
| `-p`     | show only participating or mentioned notifications      | `gh notify -ap`                                      |
| `-r`     | mark all notifications as read                          | `gh notify -r`                                       |
| `-s`     | print a static display                                  | `gh notify -an 10 -s`                                |
| `-u URL` | (un)subscribe a URL, useful for issues/prs of interest  | `gh notify -u https://github.com/cli/cli/issues/659` |
| `-w`     | display the preview window in interactive mode          | `gh notify -an 10 -w`                                |

### Key Bindings fzf

| Keys                           | Description                                         | Customization Environment Variable |
| ------------------------------ | --------------------------------------------------- | ---------------------------------- |
| <kbd>?</kbd>                   | toggle help                                         | `GH_NOTIFY_TOGGLE_HELP_KEY`        |
| <kbd>enter</kbd>               | view the selected notification in the 'less' pager  | `GH_NOTIFY_VIEW_KEY`               |
| <kbd>tab</kbd>                 | toggle notification preview                         | `GH_NOTIFY_TOGGLE_PREVIEW_KEY`     |
| <kbd>shift</kbd><kbd>tab</kbd> | resize the preview window                           | `GH_NOTIFY_RESIZE_PREVIEW_KEY`     |
| <kbd>shift</kbd><kbd>↑↓</kbd>  | scroll the preview up/ down                         |                                    |
| <kbd>ctrl</kbd><kbd>a</kbd>    | mark all displayed notifications as read and reload | `GH_NOTIFY_MARK_ALL_READ_KEY`      |
| <kbd>ctrl</kbd><kbd>b</kbd>    | browser                                             | `GH_NOTIFY_OPEN_BROWSER_KEY`       |
| <kbd>ctrl</kbd><kbd>d</kbd>    | view diff                                           | `GH_NOTIFY_VIEW_DIFF_KEY`          |
| <kbd>ctrl</kbd><kbd>p</kbd>    | view diff in patch format                           | `GH_NOTIFY_VIEW_PATCH_KEY`         |
| <kbd>ctrl</kbd><kbd>r</kbd>    | reload                                              | `GH_NOTIFY_RELOAD_KEY`             |
| <kbd>ctrl</kbd><kbd>t</kbd>    | mark the selected notification as read and reload   | `GH_NOTIFY_MARK_READ_KEY`          |
| <kbd>ctrl</kbd><kbd>x</kbd>    | write a comment with the editor and quit            | `GH_NOTIFY_COMMENT_KEY`            |
| <kbd>ctrl</kbd><kbd>y</kbd>    | toggle the selected notification                    | `GH_NOTIFY_TOGGLE_KEY`             |
| <kbd>esc</kbd>                 | quit                                                | `GH_NOTIFY_EXIT_KEY`               |

### Table Format

| Field         | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| unread symbol | indicates unread status                                      |
| time          | time of last read for unread; otherwise, time of last update |
| repo          | related repository                                           |
| type          | notification type                                            |
| number        | associated number                                            |
| reason        | trigger reason                                               |
| title         | notification title                                           |

---

## Customizations

### Fuzzy Finder (fzf)
You can customize the `fzf` key bindings by exporting `ENVIRONMENT VARIABLES` to your `.bashrc` or
`.zshrc`. For `AVAILABLE KEYS/ EVENTS`, refer to the `fzf` man page or visit
[junegunn/fzf#environment-variables](https://github.com/junegunn/fzf#environment-variables) on
GitHub.

- **NOTE**: [How to use ALT commands in a terminal on macOS?](https://superuser.com/questions/496090/how-to-use-alt-commands-in-a-terminal-on-os-x)

```sh
# ~/.bashrc or ~/.zshrc
# The examples below enable you to clear the input query with alt+c,
# jump to the first/last result with alt+u/d, refresh the preview window with alt+r
# and scroll the preview in larger steps with ctrl+w/s.
export FZF_DEFAULT_OPTS="
--bind 'alt-c:clear-query'
--bind 'alt-u:first,alt-d:last'
--bind 'alt-r:refresh-preview'
--bind 'ctrl-w:preview-half-page-up,ctrl-s:preview-half-page-down'"
```

#### GH_NOTIFY_FZF_OPTS
This environment variable lets you specify additional options and key bindings to customize the
search and display of notifications. Unlike `FZF_DEFAULT_OPTS`, `GH_NOTIFY_FZF_OPTS` specifically
applies to the `gh notify` extension.

```sh
# --exact: Enables exact matching instead of fuzzy matching.
GH_NOTIFY_FZF_OPTS="--exact" gh notify -an 5
```

```sh
# With the height flag and ~, fzf adjusts its height based on input size without filling the entire screen.
# Requires fzf +0.34.0
GH_NOTIFY_FZF_OPTS="--height=~100%" gh notify -an 5
```

#### Modifying Keybindings
You can also customize the keybindings created by this extension to avoid conflicts with
the ones defined by `fzf`. For example, change `ctrl-p` to `ctrl-u`:

```sh
GH_NOTIFY_VIEW_PATCH_KEY="ctrl-u" gh notify
```

Or, switch the binding for toggling a notification and toggling the preview.
```sh
GH_NOTIFY_TOGGLE_KEY="tab" GH_NOTIFY_TOGGLE_PREVIEW_KEY="ctrl-y" gh notify
```

To reassign the exit key from `esc` to `ctrl-c` and ignore the `esc` key, use:
```sh
GH_NOTIFY_FZF_OPTS="--bind 'esc:ignore'" GH_NOTIFY_EXIT_KEY="ctrl-c" gh notify
```

**NOTE:** The assigned key must be a valid key listed in the `fzf` man page:

```sh
man --pager='less -p "^\s+AVAILABLE_KEYS"' fzf
```

### GitHub Command Line Tool (gh)
In the `gh` tool's config file, you can specify your preferred editor. This is particularly useful
when you use the <kbd>ctrl</kbd><kbd>x</kbd> hotkey to comment on a notification.

```sh
# To see more details
gh config
# For example, you can set the editor to Visual Studio Code or Vim.
gh config set editor "code --wait"
gh config set editor vim
```
