# arch-t480s
Installation notes for Arch Linux on a ThinkPad t480s.

- [Qemu VM](qemu.md)
- [Base Installation](base_install.md)
- [i3 Installation](i3_install.md)

## Troubleshooting

### Bluetooth

```
sudo pacman -S bluez bluez-utils pulseaudio-bluetooth
pulseaudio -k
pulseaudio --start
systemctl start bluetooth.service
```

Connect device

```
bluetoothctl
power on
scan on
pair DEVICE
trust DEVICE
connect DEVICE
scan off
```
