### Install Xorg
```
sudo pacman -S xorg xorg-xinit xorg-xclock xterm
```

### Copy xinit config
```
cp /etc/X11/xinit/xinitrc ~/.xinitrc
```

### Install i3
Exit GUI

```
sudo pacman -S i3 i3status adobe-source-code-pro-fonts
```

### Modify xinitrc
```
nvim ~/.xinitrc

#!/bin/bash
exec i3
```

**Enjoy**
