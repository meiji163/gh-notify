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

| Keys                           | Description                                         |
| ------------------------------ | --------------------------------------------------- |
| <kbd>?</kbd>                   | toggle help                                         |
| <kbd>enter</kbd>               | view the selected notification in the 'less' pager  |
| <kbd>tab</kbd>                 | toggle notification preview                         |
| <kbd>shift</kbd><kbd>tab</kbd> | resize the preview window                           |
| <kbd>shift</kbd><kbd>↑↓</kbd>  | scroll the preview up/ down                         |
| <kbd>ctrl</kbd><kbd>a</kbd>    | mark all displayed notifications as read and reload |
| <kbd>ctrl</kbd><kbd>b</kbd>    | browser                                             |
| <kbd>ctrl</kbd><kbd>d</kbd>    | view diff                                           |
| <kbd>ctrl</kbd><kbd>p</kbd>    | view diff in patch format                           |
| <kbd>ctrl</kbd><kbd>r</kbd>    | reload                                              |
| <kbd>ctrl</kbd><kbd>t</kbd>    | mark the selected notification as read and reload   |
| <kbd>ctrl</kbd><kbd>x</kbd>    | write a comment with the editor and quit            |
| <kbd>esc</kbd>                 | quit                                                |

### Table Format

| Field         | Description                                      |
| ------------- | ------------------------------------------------ |
| unread symbol | indicates unread status                          |
| time          | last read (unread &#9679;) otherwise update time |
| repo          | related repository                               |
| type          | notification type                                |
| number        | associated number                                |
| reason        | trigger reason                                   |
| title         | notification title                               |

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
