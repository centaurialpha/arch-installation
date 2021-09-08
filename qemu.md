### Create an image
```
qemu-img create -f qcow2 Image.img 10G
```

### Execute VM
```
qemu-system-x86_64 -enable-kvm -cdrom arch.iso -boot menu=on -drive file=Image.img -m 2G -bios /usr/share/edk2-ovmf/x64/OVMF_CODE.fd -cpu host -vga virtio -display sdl,gl=on
```
