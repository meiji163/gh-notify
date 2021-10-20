# GitHub CLI Notification Extension 

[gh](https://github.com/cli/cli) extension to interact with GitHub notifications.

## Install
```
gh extension install meiji163/gh-notify
```

Install [fzf](https://github.com/junegunn/fzf) for interactive mode.

## Usage 
```
Usage: gh notify [--flags]

View and search and GitHub notifications.
Select a pull request or issue to get more info on it.

Flags:
    -s      print a static display
    -n      max number of notifications to show (default 30)
    -p      boolean flag to only participating or mention notifications
    -a      boolean flag to include read notifications
```

![demo](https://i.imgur.com/Lv308LC.gif)

## TODO
- mark notifications as (un)read
- add interaction for discussion threads, actions, etc. 
