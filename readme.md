# GitHub CLI Notification Extension

[gh](https://github.com/cli/cli) extension to interact with GitHub notifications.

## Install

```
gh extension install meiji163/gh-notify
```

Install the [Fuzzy Finder (fzf)](https://github.com/junegunn/fzf#installation) for interactive mode.

## Usage

![demo](https://user-images.githubusercontent.com/92653266/186245012-46560f5f-e44f-45fe-8f71-86009c61305f.gif)

```
gh notify [Flags]
```

| Flags  | Description                                             | Example              |
| ------ | ------------------------------------------------------- | -------------------- |
| <none> | show all unread notifications                           | gh notify            |
| -a     | show all (read/ unread) notifications                   | gh notify -a         |
| -r     | mark all notifications as read                          | gh notify -r         |
| -e     | exclude notifications matching a string (REGEX support) | gh notify -e "MyJob" |
| -f     | filter notifications matching a string (REGEX support)  | gh notify -f "Repo"  |
| -s     | print a static display                                  | gh notify -as        |
| -n NUM | max number of notifications to show                     | gh notify -an 10     |
| -p     | show only participating or mentioned notifications      | gh notify -ap        |
| -w     | display the preview window in interactive mode          | gh notify -an 10 -w  |
| -h     | show the help page                                      | gh notify -h         |

### Key Bindings fzf

| Keys                           | Description                                         |
| ------------------------------ | --------------------------------------------------- |
| <kbd>?</kbd>                   | toggle help                                         |
| <kbd>enter</kbd>               | print and mark the notification as read and quit    |
| <kbd>tab</kbd>                 | toggle preview notification                         |
| <kbd>shift</kbd><kbd>tab</kbd> | change preview window size                          |
| <kbd>shift</kbd><kbd>↑↓</kbd>  | scroll the preview up/ down                         |
| <kbd>ctrl</kbd><kbd>b</kbd>    | open notification in the browser                    |
| <kbd>ctrl</kbd><kbd>d</kbd>    | view diff                                           |
| <kbd>ctrl</kbd><kbd>p</kbd>    | view diff in patch format                           |
| <kbd>ctrl</kbd><kbd>r</kbd>    | mark all displayed notifications as read and reload |
| <kbd>ctrl</kbd><kbd>t</kbd>    | mark notification as read and reload                |
| <kbd>ctrl</kbd><kbd>x</kbd>    | write a comment with the editor and quit            |
| <kbd>esc</kbd>                 | quit                                                |

---
## Customizations

### Fuzzy Finder (fzf)
Customize fzf key bindings by exporting `ENVIRONMENT VARIABLES` to your `.bashrc`/`.zshrc`. See the man page (`man fzf`) for `AVAILABLE KEYS/ EVENTS` or [junegunn/fzf#environment-variables](https://github.com/junegunn/fzf#environment-variables) on GitHub for more details.

- NOTE: [How to use ALT commands in a terminal on macOS?](https://superuser.com/questions/496090/how-to-use-alt-commands-in-a-terminal-on-os-x)

```sh
# ~/.bashrc or ~/.zshrc
# The following examples allow you to clear the input query with alt+c,
# jump to the first/last result with alt+u/d, refresh the preview window with alt+r
# and scroll the preview in larger steps with ctrl+w/s.
export FZF_DEFAULT_OPTS="
--bind 'alt-c:clear-query'
--bind 'alt-u:first,alt-d:last'
--bind 'alt-r:refresh-preview'
--bind 'ctrl-w:preview-half-page-up,ctrl-s:preview-half-page-down'"`
```

### GitHub command line tool (gh)
In the configuration file of the `gh` tool you can set your preferred editor. This is handy when you use the <kbd>ctrl</kbd><kbd>x</kbd> hotkey to write a comment on a notification.

```sh
# See more details
gh config
# For example, set the editor to Visual Studio Code or Vim.
gh config set editor "code --wait"
gh config set editor vim
```
