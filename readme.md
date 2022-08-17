# GitHub CLI Notification Extension

[gh](https://github.com/cli/cli) extension to interact with GitHub notifications.

## Install
```
gh extension install meiji163/gh-notify
```

Install [fzf](https://github.com/junegunn/fzf) for interactive mode.

## Usage
```
> gh notify # view notifications
> gh notify -r # mark notifications as read
> gh notify -h # help info
Usage: gh notify [--flags]

View and search GitHub notifications.
Select a pull request or issue to get more info on it.

Flags:
    -a      include all notifications
    -w      display the fzf preview window (default: hidden)
    -e      exclude notifications matching a string
            Ex. gh notify -e "MyDayJob"
    -f      filter to only notifications matching a string
            Ex. gh notify -f "CoolRepo"
    -n      max number of notifications to show (default 30)
    -p      show only participating or mention notifications
    -r      mark all notifications as read
    -s      print a static display

Note: -e and -f both support GNU regular expressions.
```

![demo](https://user-images.githubusercontent.com/92653266/185198672-6ae90682-b891-4fc4-b51e-0efbce427b46.gif)
