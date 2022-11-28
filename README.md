# Remove Poweroff From Shell History

I regularly, unfortunately, power off my computer by mistake due to use up arrow key to go 
back in the history. 

So I wrote a `cronjob` to remove all `poweroff`, `shutdown`, `reboot` and `halt` commands.

# Requirements

![Cronie](https://shields.io/badge/Cronie-red)

Cronie required to use that scripts. I you don't want  to use `cronjobs`, you can simply add that lines your ~/.bashrc or ~/.zshrc by cutting "@reboot".

# Installation

Just copy the command you fit your shell program and add that line to your `crontab`:

```awk
# for oh-my-zsh
@reboot awk '!/: [0-9]+:[0-9]+;(poweroff|shutdown|reboot|halt) ?.*/' ~/.zsh_history > /tmp/.zsh_history && mv /tmp/.zsh_history ~/.zsh_history

# for bash
@reboot awk '!/(poweroff|shutdown|reboot|halt) ?.*/' ~/.bash_history > /tmp/.bash_history && mv /tmp/.bash_history ~/.bash_history
```

To open `crontab`  type: 

```sh
crontab -e
```

