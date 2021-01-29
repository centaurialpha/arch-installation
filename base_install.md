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
- `g`: New GPT partition
- `n`: Add new partition
- `t`: Change partition type
- `w`: Write changs
