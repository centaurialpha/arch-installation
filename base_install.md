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
# mkfs -F32 /dev/sda1
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
# pacstrap /mnt base linux linux-firmware
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
```
# pacman -S nano
```

Edit /etc/locale.gen and uncomment `en_US.UTF-8 UTF8`
```
# locale-gen
```

Create `/etc/locale.conf` with:
```
LANG=en_US.UTF-8
```

13. Create hostname file
```
# echo HOSTNAME > /etc/hostname
```

14. Edit `/etc/hosts`
```
127.0.0.1	localhost
::1		localhost
127.0.1.1	myhostname.localdomain	myhostname
```

