### Install Xorg
```
sudo pacman -S xorg xorg-xinit i3 i3status adobe-source-code-pro-fonts
```

### Xinitrc
```
cp /etc/X11/xinit/xinitrc ~/.xinitrc
```

```
nvim ~/.xinitrc

#!/bin/bash
exec i3
```

### Start i3
```
startx
```

**Enjoy**
