### Install minimal xorg
```
sudo pacman -S xorg-server xorg-xinit
```

### Install qtile from srouces
```
paru -S qtile-git qtile-extras
```

### Install some packages
```
sudo pacman -S starship ttf-cascadia-code exa bat tmux ttf-font-awesome dunst otf-hermit picom
```

### Create xinitrc
```
nvim ~/.xinitrc

#!/bin/bash

exec qtile start
```
