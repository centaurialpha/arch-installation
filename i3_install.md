### Install Xorg
```
sudo pacman -S xorg xorg-xinit xorg-xclock xterm
```

### Copy xinit config
```
cp /etc/X11/xinit/xinitrc ~/.xinitrc
```

### Test GUI
```
startx
```

### Install font
Exit GUI

```
sudo pacman -S adobe-source-code-pro-fonts
```

### Modify xinitrc
```
nvim ~/.xinitrc

#!/bin/bash
exec i3
```

**Enjoy**
