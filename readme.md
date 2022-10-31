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
gh notify [-Flag]
```

| Flag   | Description                                             | Example              |
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

### HotKeys for interactive mode with Fuzzy Finder (fzf)

| HotKey   | Description                                       |
| -------- | ------------------------------------------------- |
| ?        | toggle help                                       |
| tab      | toggle preview notification                       |
| enter    | print notification and exit                       |
| shift+↑↓ | scroll the preview up/ down                       |
| ctrl+b   | open notification in browser                      |
| ctrl+r   | mark all displayed notifications as read and exit |
| ctrl+x   | write a comment with the editor and exit          |
| esc      | exit                                              |

## Customizations

### Fuzzy Finder (fzf)
Customize fzf colors and key bindings by exporting `ENVIRONMENT VARIABLES` to your `.zshrc`/`.bashrc`. See the man page (`man fzf`) for `AVAILABLE KEYS/ EVENTS` or [junegunn/fzf#environment-variables](https://github.com/junegunn/fzf#environment-variables) on GitHub for more details.

- NOTE: [How to use ALT commands in a terminal on macOS?](https://superuser.com/questions/496090/how-to-use-alt-commands-in-a-terminal-on-os-x)

```zsh
# ~/.zshrc
# The following examples allow you to clear the input query with alt+c,
# jump to the first/last result with alt+u/d, refresh the preview window with alt+r
# and scroll the preview in larger steps with ctrl+w/s.
export FZF_DEFAULT_OPTS="
--bind 'alt-c:clear-query'
--bind 'alt-u:first,alt-d:last'
--bind 'alt-r:refresh-preview'
--bind 'ctrl-w:preview-half-page-up,ctrl-s:preview-half-page-down'
..."`

```

### GitHub command line tool (gh)
In the configuration file of the `gh` tool you can set your preferred editor. This is handy when you use the interactive mode to write a comment on a notification.

```zsh
# See more details
gh config
# For example, set the editor to Visual Studio Code or Vim.
gh config set editor "code --wait"
gh config set editor vim
```
