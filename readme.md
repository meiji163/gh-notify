# GitHub CLI Notification Extension 

[gh](https://github.com/cli/cli) extension to interact with GitHub notifications.

## Install
```
gh extension install meiji163/gh-notify
```

Install [fzf](https://github.com/junegunn/fzf) for interactive mode.

## Usage 
```
> gh notify # view notifs
> gh notify -r # mark notifs as read
> gh notify -h # help info 
Usage: gh notify [--flags]

View and search and GitHub notifications. 
Select a pull request or issue to get more info on it.

Flags:
    -a      include all notifications 
    -r      mark all notifications as read 
    -s      print a static display
    -p      show only participating or mention notifications
    -n      max number of notifications to show (default 30)
```

![demo](https://i.imgur.com/Lv308LC.gif)
