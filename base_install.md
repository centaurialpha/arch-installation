1. Disable secure boot.
2. Connect to internet.
```
# iwctl station wlan0 connect NAME
# ping 8.8.8.8
```

3. Set keyboard layout
```
# loadkeys us
```

4. Update system clock
```
# timedatectl set-ntp true
```

5. Partition the disks

Using fdisk create the following layout.
```
# fdisk /dev/sda
```

| Partition | Type | Size  |
|-----------|------|-------|
| /dev/sda1 | EFI  | +550M |
| /dev/sda2 | swap | +4G   |
| /dev/sda3 | ext4 | free  |

Commands:
- `g`: New GPT partition.
- `n`: Add new partition.
- `t`: Change partition type.
- `w`: Write changes.

6. Format partitions
```
# mkfs.fat -F32 /dev/sda1
# mkswap /dev/sda2
# mkfs.ext4 /dev/sda3
```

7. Mount the file system
```
# mount /dev/sda3
# swapon /dev/sda2
```

8. Install base
```
# pacstrap /mnt base linux linux-firmware neovim
```

9. Configure Fstab
```
# genfstab -U /mnt >> /mnt/etc/fstab
```

10. Change root into the new system
```
# arch-chroot /mnt
```

11. Set the time zone
```
# ln -sf /usr/share/zoneinfo/America/Argentina/Catamarca /etc/localtime
# hwclock --systohc
```

12. Localization

Edit /etc/locale.gen and uncomment `en_US.UTF-8 UTF8`
```
# locale-gen
```

```
# echo LANG=en_US.UTF-8 > /etc/locale.conf
```

13. Create hostname file
```
# echo arch > /etc/hostname
```

14. Edit `/etc/hosts`
```
127.0.0.1	localhost
::1		localhost
127.0.1.1	arch.localdomain	arch
```

15. Set root password

```
# passwd
```

16. Create user and set password

```
# useradd gabox
# passwd gabox
# usermod -aG wheel,audio,video,optical,storage gabox
```

17. Configure sudo

```
# pacman -S sudo
# EDITOR=nvim visudo  # uncomment %wheel ALL=(ALL) ALL
```

18. Install grub stuff

```
# pacman -S grub efibootmgr dosfstools os-prober mtools
```

19. Create and mount boot partition

```
# mkdir /boot/EFI
# mount /dev/sda1 /boot/EFI
```

20. Install grub

```
# grub-install --target=x86_64-efi --bootloader-id=grub_uefi --recheck
# grub-mkconfig -o /boot/grub/grub.cfg
```

**The base system is installed. It would be a good idea to install some network manager.**

21. Install network stuff

```
# pacman -S iwd dhcpcd
```

22. Reboot system

```
# exit
# umount -l /mnt
# reboot
```
