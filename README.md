# riceswap
[heavily wip] hyprland/quickshell rice swappper cli tool.

## no documentation yet, but try it out. 
 <kbd>run riceswap -h for help</kbd>
---
its fully crossplatform as its just a bash script.
### installation
```sh
git clone https://github.com/im-vihar/riceswap.git
cd riceswap && rm -f ~/.local/bin/riceswap && chmod +x riceswap && mv riceswap ~/.local/bin

riceswap
```
### inititialize
> [!WARNING]
> err there's a gray area where if you run this with files actually inside ~/.config/hypr and /quickshell you may loose them. just create a new profile with `riceswap create <name>` and move your hypr and quickshell folder into `~/.config/riceswap/profiles<name>`
```sh
riceswap init
```

