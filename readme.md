# GitHub CLI Notification Extension

[gh](https://github.com/cli/cli) extension to interact with GitHub notifications.

## Install

```
gh extension install meiji163/gh-notify
```

Install the [Fuzzy Finder (fzf)](https://github.com/junegunn/fzf#installation) for interactive mode.

## Usage

![demo](https://user-images.githubusercontent.com/92653266/185198672-6ae90682-b891-4fc4-b51e-0efbce427b46.gif)

### Flags

```
gh notify [-Flag]
```

| Flag   | Description                                                          | Example              |
| ------ | -------------------------------------------------------------------- | -------------------- |
| <none> | show all unread notifications                                        | gh notify            |
| -a     | show all (read/ unread) notifications                                | gh notify -a         |
| -r     | mark all notifications as read                                       | gh notify -r         |
| -e     | exclude notifications matching a string (regular expression support) | gh notify -e "MyJob" |
| -f     | filter the search to a specific user (regular expression support)    | gh notify -f "Repo"  |
| -s     | print a static display                                               | gh notify -as        |
| -n     | max number of notifications to show (default 30)                     | gh notify -an        |
| -p     | show only participating or mentioned notifications                   | gh notify -ap        |
| -w     | display the preview window in interactive mode (default hidden)      | gh notify -an 10 -w  |
| -h     | show the help page                                                   | gh notify -h         |

### HotKeys for interactive mode with Fuzzy Finder (fzf)

| HotKey   | Description                              |
| -------- | ---------------------------------------- |
| enter    | print notification and exit              |
| tab      | preview notification                     |
| shift+↑↓ | scroll the preview up/ down              |
| ctrl+b   | open notification in browser             |
| ctrl+r   | mark all notifications as read and exit  |
| ctrl+x   | write a comment with the editor and exit |
| esc      | exit                                     |

## Customization by modifing environment variables

### Fuzzy Finder (fzf)
Customize fzf colors and key bindings by exporting `ENVIRONMENT VARIABLES` to your `.zshrc`/`.bashrc`. See the man page (`man fzf`) or the [fzf README](https://github.com/junegunn/fzf#environment-variables) on GitHub for more details.

```zsh
# .zshrc
# This example allows you to scroll the preview in larger steps with ctrl+w/s.
export FZF_DEFAULT_OPTS="
--bind 'ctrl-w:preview-half-page-up,ctrl-s:preview-half-page-down'"`
```

### GitHub command line tool (gh)
In the configuration file of the `gh` tool you can set your preferred editor. This is handy when you use the interactive mode to write a comment on a message.

```zsh
# See more details
gh config
# For example, set the editor to Visual Studio Code or Vim.
gh config set editor "code --wait"
gh config set editor vim
```
