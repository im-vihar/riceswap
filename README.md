# riceswap
[heavily wip] hyprland/quickshell rice swappper cli tool.

## no documentation yet, but try it out. 
 <kbd>run riceswap -h for help</kbd>
---
its fully crossplatform as its just a bash script.
### installation
```sh
git clone https://github.com/im-vihar/riceswap.git ~/.cache/riceswap
cd ~/.cache/riceswap && rm -f ~/.local/bin/riceswap && chmod +x riceswap && mv riceswap ~/.local/bin && riceswap && rm -rf ~/.cache/riceswap
```
### inititialize
> [!WARNING]
> err there's a gray area where if you run this with files actually inside ~/.config/hypr and /quickshell you may loose them. just create a new profile with `riceswap create <name>` and move your hypr and quickshell folder into `~/.config/riceswap/profiles<name>`
```sh
riceswap init
```
<details>
<summary>custom ui (using rofi/fuzzel)</summary>
if you're someone like me, you have multiple profiles, and so a simple switch-like keybind that just runs <kbd>riceswap set scroll</kbd> isnt enough. a simple rofi/fuzzel -dmenu script works well. and then just bind a key to run this script on press.



      
<img src="https://github.com/im-vihar/riceswap/blob/424b5fea589afd3dde7109ebc4a6e90d1f3db4ac/fuzzel.png" width="350">

### rofi:
```sh
#!/usr/bin/env bash

# Force include standard binary folders just in case
export PATH="$HOME/.local/bin:$HOME/bin:/usr/local/bin:/usr/bin:/bin:$PATH"

# 1. Parse the available profiles clean into Rofi
CHOSEN=$(riceswap list | awk 'NR>2 {print $2}' | rofi -dmenu -i -p "🍚 riceswap set" -theme-str 'entry { placeholder: "Search profiles..."; }')

# 2. If the user didn't hit Escape/cancel, apply the selected profile
if [ -n "$CHOSEN" ]; then
    riceswap set "$CHOSEN"
fi
```

### fuzzel: 
 ```sh
#!/usr/bin/env bash

# Force include standard binary folders just in case
export PATH="$HOME/.local/bin:$HOME/bin:/usr/local/bin:/usr/bin:/bin:$PATH"

# 1. Parse the available profiles clean into Fuzzel (using absolute paths or explicit PATH)
CHOSEN=$(riceswap list | awk 'NR>2 {print $2}' | fuzzel --dmenu --prompt="🍚 riceswap set: " --placeholder="Search profiles...")

# 2. If the user didn't hit Escape/cancel, apply the selected profile
if [ -n "$CHOSEN" ]; then
    riceswap set "$CHOSEN"
fi
```
</details>
