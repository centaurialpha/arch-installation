# arch-installation
Installation notes for Arch Linux on a ThinkPad t480s and MSI GF63 Thin.

- [Qemu VM](qemu.md)
- [Base Installation](base_install.md)
- [Qtile Installation](qtile_install.md)

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
