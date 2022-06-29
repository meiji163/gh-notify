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

![demo](https://i.imgur.com/Lv308LC.gif)
